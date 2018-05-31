---
layout: post
title: Memorial Notifier API
feature-img: "img/sample_feature_img.png"
thumbnail-path: "img/projects/memorial-notifier-api/jwt.png"
short-description: Rails v.5 API using JWT's

---
[Visit the Site](https://memorial-notifier-api.herokuapp.com/%20){:target="_blank"} (Note: It is an API, see ReadMe for interaction)<br>
[Source Code on Git Hub](https://github.com/samibirnbaum/Memorial-Notifier-API){:target="_blank"}
<hr color="gray">


<!-- CASE STUDY HERE -->
<!-- Summary -->
### Summary
<!--    - short and to the point -->
<!--    - starting point >>> outcome -->
This project was my venture into creating an agnostic backend. Arguably how backends should be built.

What you will find is a fully functional Ruby on Rails API, that uses Devise with JWT's for secure authentication. This type of design allows for a robust backend that can be connected to any frontend. This permits a highly flexible frontend. If you prefer Angular, be my guest. React? IOS or Android Application? The choice is yours! 

For a little bit more insight on the build visit my [Blog](https://samibirnbaum.com/2018/05/30/rails-api-with-devise-and-jwt.html) on the build.

<!--tech used-->
##### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Spec:
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Ruby <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Ruby on Rails <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; [RSpec](https://rubygems.org/gems/rspec-rails){:target="_blank"} <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; [Devise](https://rubygems.org/gems/devise){:target="_blank"} <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; [Devise-JWT](https://rubygems.org/gems/devise-jwt){:target="_blank"} <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; [rack-cors](https://rubygems.org/gems/rack-cors){:target="_blank"} <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; [active_model_serializers](https://rubygems.org/gems/active_model_serializers){:target="_blank"} <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; [Factory Bot](https://rubygems.org/gems/active_model_serializers){:target="_blank"} <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; [Figaro](https://rubygems.org/gems/figaro){:target="_blank"} <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; [ByeBug](https://rubygems.org/gems/byebug){:target="_blank"} <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Git & Git Hub <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; [Heroku](https://www.heroku.com/){:target="_blank"} <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; [Postman](https://www.getpostman.com/){:target="_blank"}

<hr color="gray">



<!-- my role  -->
### My Role
<!--    - backstory, who and why? -->
To create this application as a sole developer, working remotely, completing specific tasks outlined by a company director.

<!--    - explanation / relationship you had to the project -->
I was asked to develop an in-house application for staff to be able to record community members deaths. The idea was to automate this process and make it secure.

I used this opportunity to learn more about rails and create an API using Devise and [JWT's](https://jwt.io/){:target="_blank"}.

As a sole developer I had to manage the project holistically from beginning to end.

I used [GitHub Issues](https://github.com/samibirnbaum/Memorial-Notifier-API/issues){:target="_blank"} to create Milestones, each of which reflected a User Story, with specific issues pertaining to that feature assigned to the milestone.

Moreover, I used [HuBoard](https://huboard.com/samibirnbaum/Memorial-Notifier-API#/milestones){:target="_blank"} as a project manager tool which provides a more intuitive UI for GitHub Issues.

On top of the above I was expected to implement TDD using RSpec.

I used Git to maintain a local repository of the project and a remote repository on GitHub, and used feature branches to ensure a smooth workflow and secure version control.

Lastly, I decided to deploy my application on [Heroku](https://www.heroku.com/){:target="_blank"} using their CLI, to further enhance my knowledge of Hosting, DNS and Domain Names. 
<hr color="gray">


<!-- Problems -->

### Problems
<!--    - problems you were hired to solve -->
Building an application of this nature from scratch meant there were numerous tasks and problems that needed to be solved. Given the limited scope of this work I will attempt to name a couple to give you an insight into the generic challenges faced and my approach to them.

<!-- list 3 -->
1. &nbsp;Configure devise to accept HTTP requests made with JSON.  <br/><br/>
<!--    - -->
2. &nbsp;Authenticate a user by sending and receiving [JSON Web Tokens](https://jwt.io/){:target="_blank"}.<br/><br/>
<!----->
3. &nbsp;How can a user reset their password if they forget it.<br/>
<hr color="gray">


<!-- Solutions -->
<br>
### Solutions
<!--    - -->
1. &nbsp;Devise is built with standard Ruby on Rails applications in mind. Those which ship with the built-in rails views. As a result of this, Devise works really well out the box when making standard HTTP requests through HTML. However, it is not set up to accept JSON.

In order to get this functionality working it took a lot of tweaking, reading and trial and error! However, the final solution is actually fairly straightforward, contrary to a lot of walkthroughs you will find online which I found to be over complicated.

Underneath the hood of devise there are 3 controllers: `sessions`, `registrations` and `passwords`.

If you want to be able to hit an action in one of those controllers, you just need to tell that controller to accept JSON. That really is all there is too it!

In its most simple implementation you could just add this line to the application contoller.

{% highlight ruby %}
class ApplicationController < ActionController::API
    respond_to :json
end
{% endhighlight %}

I actually chose to do this by extending the individual controller I wanted to accept JSON requests. My reason for doing this, is because I would need to do this for some added functionality down the line, so it made sense to do it this way at this stage.

{% highlight ruby %}
class Api::SessionsController < Devise::SessionsController
    respond_to :json
end
{% endhighlight %}

Note: If you do go about it my way you will have to be careful to reflect these controller changes in your routes:

{% highlight ruby %}
Rails.application.routes.draw do
    #must be scoped and not namespaced
  scope :api, defaults: { format: :json } do 
    devise_for :users, :controllers => {sessions: 'api/sessions', registrations: 'api/registrations'}
  end
end
{% endhighlight %}

All that remains is to configure the [rack-cors gem](https://rubygems.org/gems/rack-cors){:target="_blank"}.

Open [Postman](https://www.getpostman.com/){:target="_blank"} and start seeing your requests hit the devise actions.
<br/><br/><br>
<!--    - -->
2\. &nbsp; So many aspects of this were very daunting. Even on a high-level it was really challenging to get my head around the desired outcome, and envision sessions, authentication and authorisation, conceptually.

Moreover, there are an incredible amount of articles on the internet about how to go about this, many of which have numerous comments, some saying it works and others saying it doesn't. This level of diverse opinion made it hard to know where to start or which rabbit hole to run down.

Furthermore, I was quite adamant that I wanted to have the functionality that devise ships with. What was the point of having devise if my JWT authentication system just bypassed all its functionality?

After much discovery and thought I found a [gem](https://rubygems.org/gems/devise-jwt){:target="_blank"} that professed to providing exactly what I was looking for. And it actually did just that! 

I carefully walked through the GitHub ReadMe and after days of trial and error, I was finally able to see my API come to my life.

My API worked exactly as devise did out of the box, only with HTTP requests being able to be made via JSON from anywhere.

When a user logged-in they would be sent back a secure JWT in the response header. On future requests, this JWT is expected to be in the request `header` in a `key/value` format:

`Authorization: Bearer <JWT>`

As well as this, JWT's contain a payload. Utilising this I was able to send the users id with every request to maintain some form of state and use devise's `current_user` method.

Below is an example of an HTTP request for a user to update their account details:

Method: `PUT`

Path: http://localhost:3000/api/users

Headers:

`Content-Type: application/json`

`Authorization: Bearer <JWT>`

Body:
```json
{"user":
	{
	"email":"joebloggs@gmail.com",
	"password":"strongjoe123456",
	"current_password": "joe123456"
	}
}
```

Expectations: The user needs to provide their current password, and they will be able to change their email and password. If successful response status will be `204`. If unsuccessful response status will be `422` with JSON errors in the response body.

<br/><br/>
<!-- - -->
3\. &nbsp; Normally with devise, this is as simple as clicking a link on the log-in form. But this wasn't _normal_ devise. My application was operating in API mode.

The lack of a link wasn't an issue, whichever action that link was mapped to, I could hit that same action through an HTTP request.

The real issue was how the action operated.

When a user clicks forgot password, devise sends that user a secure link to their email. The user then clicks on this link which directs them to a form view on the site to create their new password.

However, using an API we dont have any views, so the link devise sends to the user is no good for us at all.

Thus, I needed to create my own way of assisting a user who forgot their password.

The thought process was as follows:

1. Create a controller with an action that user accesses when they forget their password.
2. This action resets the users password on the database to a random string.
3. This random string is then emailed to the user.
4. The user can then log-in via the api with this new password string.
5. They can then use the update user action to change their password to something more memorable.

And here is the code in action:

{% highlight ruby %}
class Api::ResetsPasswordsController < ApplicationController
    def reset
        @user = User.find_by_email(params["user"]["email"])
        if @user.present?
            @temp_password = SecureRandom.hex(6)
            User.update(@user.id, password: @temp_password)
            UserNotifierMailer.send_password_reset_email(@user, @temp_password).deliver
            render json: {message: "email instructions have been sent to #{params["user"]["email"]} to reset password"}
        else
            render json: {message: "email '#{params["user"]["email"]}' is invalid"}, status: :unprocessable_entity
        end
    end
end
{% endhighlight %}

A quick tweak to my routes: 

{% highlight ruby %}
Rails.application.routes.draw do
  scope :api, defaults: { format: :json } do
    devise_for :users, :controllers => {sessions: 'api/sessions', registrations: 'api/registrations'}
    post 'reset_password', to: 'api/resets_passwords#reset'
  end
end
{% endhighlight %}

And now a user would be able to access their account if they forgot their password.
<br/><br/>
<!--    - -->
<hr color="gray">



<!-- Results -->

### Results
<!--    - how you tested -->
My main form of testing for my rails application was using RSpec. This helped me to catch any bugs far quicker and meant I didn't need to be overly concerned when refactoring my code or changing other features in the application. I also tested things using `IRB`, the `rails console`, [Byebug](https://github.com/deivid-rodriguez/byebug){:target="_blank"} and [Postman](https://www.getpostman.com/){:target="_blank"}, which proved invaluable. <br>
<!--    - did you get desired outcome -->

I was thrilled with the outcome of the application. I didn't think it would be possible to build the API and authentication in the way I wanted to, and having done that, I now have code I could re-use to do it again!
<br/><br/>
<!--    - others reviews -->
Feedback from my codementor was positive.
<hr color="gray">


<!-- Conclusion -->

### Conclusion
<!--    - What were your doubts going into the project? -->
I was really being challenged with this project to use my own initiative and external resources right from the get go. I had no external guidance, I was the developer, designer, project manager all in one. Moreover, the concept of what I was trying to do with Devise and JWT was beyond the teachings of my course, and even my mentor hadn't tried something like this before.
<!--    - What surprised you the most? -->

The biggest surprise was making a get request to log-in and seeing a JWT being sent back in the response header! I just didn't think I would get it working, let alone with all the functionality of devise. <br><br>
<!--    - What would you have done differently? -->
<!--    - What did you learn while doing this project? -->
The biggest and most valuable learning curve whilst undertaking this project, was probably in my own self-confidence. I had the audacity to try something even my mentor wasn't so keen on and with the help of numerous online articles and my own debugging I was able to get there in the end. 

<!--    - How will you use that information in the future? -->
Going forward, this experience will be invaluable in giving me the confidence to try experiment with the most modern technologies, break them, put them back together and break them again! I feel like I really pushed devise and rails API mode to its limit. Furthermore, I now have the code that I can implement to get an API up and running with JWT's and devise, which is a great way to engineer things on the backend.





