---
layout: post
title: Dependeny Injection 💉 ⚽
---

Fact: Objects will very often depend on other objects.

<!--more-->

Dependency is not something we can avoid. 

However, we can try to make that dependency as loose as possible utilising a pattern called Dependency Injection.

Lets have a look at an example which does not use dependency injection first. 


{% highlight ruby %}

class TottenhamHostspurFootballClub
  def play_a_match
    striker = HarryKane.new
    
    start(striker)
  end
end

class HarryKane
  def score
    #...
  end
end

{% endhighlight %}

Looking at the code above we can see that in order for TottenhamHostpur(Spurs) to play a match they **need** Harry Kane.
This is a really restrictive tightly coupled dependency.
This means that without a striker called Harry Kane, Spurs would not be able to play a match.

Imagine Harry Kane was injured, or worse, sold to a bigger club with more potential for trophies 😢.

When Spurs would try to play a match they would not be able to do so.

{% highlight ruby %}
  TottenhamHotspurFootballClub.new.play_a_match
  # HarryKaneGoneError
{% endhighlight %}

Our `TottenhamHotspurFootballClub` class is pretty unflexible and relies heavily on `HarryKane`.

So how could Dependency Injection allow Spurs to survive and keep playing even if Harry Kane was unavailable.

{% highlight ruby %}

class TottenhamHostspurFootballClub
  
  def initialize(striker = nil)
    @striker = striker || HarryKane.new
  end
  
  def play_a_match
    striker = @striker
    
    start(striker)
  end
end

class HarryKane
  def score
    #...
  end
end

{% endhighlight %}

Ok so now things look a little more flexible.

Of course Spurs are still dependent on a striker, we can't avoid that.

But they are no longer tightly coupled to Harry Kane as being the only striker.

So we could do something like this:

{% highlight ruby %}
  spurs = TottenhamHotspurFootballClub.new(LucasMoura.new)
  spurs.play_a_match
{% endhighlight %}

One of the key things here is that the `TottenhamHotspurFootballClub` class doesn't really need to care much about who or what the striker is, it can get on
with doing its thing, only being concerned that it has received a striker.

Bonus: This would also help us test the `TottenhamHotspurFootballClub` class in isolation 👊.


