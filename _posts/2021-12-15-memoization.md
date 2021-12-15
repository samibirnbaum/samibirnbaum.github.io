---
layout: post
title: When Memoization met DRY 💕
---

Let's go on a journey into the world of memoization through the medium of ~~dance~~ Rails...

<!--more-->

Once upon a time there was a controller with 3 typical methods:

```Ruby
class UserController
  def index
    clan = Clan.find(params[:clan_id])
    users = clan.users # a user belongs to a clan and a clan has many users

    render locals: {users: users, clan: clan}
  end

  def new
    clan = Clan.find(params[:clan_id])
    user = User.new
    render locals: {user: user, clan: clan}
  end

  def create
    clan = Clan.find(params[:clan_id])
    user = clan.users.new(user_params)

    if user.save
      redirect_to ...
    else
      render :new
    end

  end

  private

  def user_params
    params.require(:user).permit(:name, :power)
  end
end

```

And all was well and good until 'DRY' came along and said "No, not by the hairs on my chinny chin chin..."

In all 3 methods we have the exact same line of code `clan = Clan.find(params[:clan_id])`

Fear not, we can clean this up by using a `before_action` to do the exact same thing:

```Ruby
class UserController
  before_action :set_clan
  
  def index
    users = clan.users

    render locals: {users: users, clan: clan}
  end

  def new
    user = User.new
    render locals: {user: user, clan: clan}
  end

  def create
    user = clan.users.new(user_params)

    if user.save
      redirect_to ...
    else
      render :new
    end

  end

  private

  def user_params
    params.require(:user).permit(:name, :power)
  end
  
  def set_clan
    clan = Clan.find(params[:clan_id])
  end
end

```

"DRY" was happy with this and managed to calm down, until "Memoization" came along and said what if I can get rid of your `before_action` altogether 🤯

Check this out =>


```Ruby
class UserController  
  def index
    users = clan.users

    render locals: {users: users, clan: clan}
  end

  def new
    user = User.new
    render locals: {user: user, clan: clan}
  end

  def create
    user = clan.users.new(user_params)

    if user.save
      redirect_to ...
    else
      render :new
    end

  end

  private

  def user_params
    params.require(:user).permit(:name, :power)
  end
  
  def clan
    Clan.find(params[:clan_id])
  end
end

```

Notice what we did?

We removed the `before_action` and changed the `set_clan` method to be called `clan`.

This means that anytime the code calls `clan` it will not be calling a variable but rather the `clan` method.

But hold on a second, I spot a performance issue....

Take a look at the index method:

```Ruby
def index
  users = clan.users

  render locals: {users: users, clan: clan}
end

```

We call `clan` 2 times which means we will be hitting our database twice in order to retrieve the `Clan` record from the database.

Enter "Memoization"...

This'll fix it 🪛

```Ruby
 def clan
   @clan ||= Clan.find(params[:clan_id])
 end

```

Great! But this is not easy to read, so what is this wizadry? 🧙‍♂️

Lets write the same method without the `||=`

```Ruby
 def clan
    if @clan.present?
      @clan
    else
      @clan = Clan.find(params[:clan_id])
      @clan
    end
  end
    
```

Now this is more readable.

Essentially when the `clan` method gets called for the first time here `users = clan.users` the `@clan` varaible will be `nil`. 

This means it will move to the `else` block and assign the `@clan` instance variable to the database record.

When it gets called a second time at `render locals: {users: users, clan: clan}` `@clan` will be present so it will just return `@clan` and not hit the database again.

Not only is this DRY, but it also means we don't have to use a `before_action` and we learnt a cool way to utilise Memoization.

The End. 👊
