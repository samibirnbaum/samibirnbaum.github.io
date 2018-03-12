---
layout: post
title: Kele
feature-img: "img/sample_feature_img.png"
thumbnail-path: "img/projects/kele/ruby-gems.png"
short-description: An API Client Ruby Gem

---

[Source Code on Git Hub](https://github.com/samibirnbaum/kele){:target="_blank"}
<hr color="gray">


<!-- CASE STUDY HERE -->
<!-- Summary -->
### Summary
<!--    - short and to the point -->
<!--    - starting point >>> outcome -->
A really interesting project. 

Welcome to Kele, a **Ruby Gem**<sup id="a1">[1](#RG)</sup> API Client<sup id="a2">[2](#AC)</sup> that allows users to access [Blocs API](https://blocapi.docs.apiary.io/#){:target="_blank"}.

Bloc's API provides an external facing JSON Web Token authorized gateway to the Bloc application. Technically it could be accessed via [cURL](https://curl.haxx.se/){:target="_blank"}, but an API client can manage the low-level details of making requests and handling responses. Packaging this functionality in a Ruby Gem would allow developers easy access to and use of the student endpoints of Bloc's API.

<!--tech used-->
##### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Spec:
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Ruby <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; [HTTParty](https://github.com/jnunemaker/httparty){:target="_blank"} <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; [PRY](https://github.com/pry/pry){:target="_blank"} <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Git & Git Hub

**This is not supposed to be a  finished product** but was part of the learning process of my web development course with [Bloc](https://www.bloc.io/){:target="_blank"} covering core programming topics.
<hr color="gray">



<!-- my role  -->
### My Role
<!--    - backstory, who and why? -->
To create this API Client as a sole developer, working remotely, completing specific tasks outlined by Bloc.

<!--    - explanation / relationship you had to the project -->
It was time to become a creator of a Ruby Gem. I had used gems throughout all my projects to take advantage of other developers great work, it was now time to repay the favour.

I enjoy getting to the bottom of things and seeing what's "under the hood", so this was an enjoyable opportunity to get my head around what really goes into producing a workable Ruby Gem; succinct code and clear guidance in `README.md`.

I was provided with User Stories <sup id="a3">[3](#UserStories)</sup> that I had to comprehend and complete.
* As a user, I want to initialize and authorize Kele with a Bloc username and password
* As a user, I want to retrieve the current user as a JSON blob
* As a user, I want to retrieve a list of my mentor's availability
* As a user, I want to retrieve roadmaps and checkpoints
* As a user, I want to retrieve a list of my messages, respond to an existing message, and create 
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;a new message thread
* As a user, I want to submit checkpoint assignments

Although, the user described above is the expectations of the end-user, it was important to keep in mind that my actual code base would be used by a developer in their own code. Thus, my focus was to achieve the above _functionality_, not to display it to the user on the frontend in any manner, that would be at the discretion of the developer using my Ruby Gem.

I used Git to maintain a local repository of the project and a remote repository on GitHub, and used feature branches to ensure a smooth workflow and secure version control.
<hr color="gray">


<!-- Problems -->

### Problems
<!--    - problems you were hired to solve -->
<!-- list 3 -->
1. &nbsp;Initialize and authorize Kele with a Bloc username and password. In simple terms, create a 
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;class that takes in a users username and password, and in doing so, gets the authentication
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;token that is needed for making future requests to Blocs API.  <br/><br/>
<!--    - -->
2. &nbsp;Retrieve the current user from the Bloc API as a JSON blob.<br/><br/>
<!----->
3. &nbsp;Add clear guidance and instructions to the `README.md` file of your Ruby Gem for other 
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;developers.<br/>
<hr color="gray">


<!-- Solutions -->
<br>
### Solutions
<!--    - -->
1. &nbsp; First and foremost my Ruby Gem would need a `.gemspec` file.

A gemspec defines metadata about your RubyGem like its name, version, and author.

{% highlight ruby %}
Gem::Specification.new do |s|
    s.name          = 'kele'
    s.version       = '0.0.1'
    s.date          = '2018-22-02'
    s.summary       = 'Kele API Client'
    s.description   = 'An API client for the Bloc API'
    s.authors       = ['Sami Birnbaum']
    s.email         = 'samibirnbaum1@gmail.com'
    s.files         = ['lib/kele.rb', 'lib/kele/roadmap.rb']
    s.require_paths = ["lib"]
    s.homepage      = 'https://github.com/samibirnbaum/kele'
    s.license       = 'MIT'
    s.add_runtime_dependency 'httparty', '~> 0.13'
    s.add_runtime_dependency 'json', '~> 1.8', '>= 1.8.3'
  end
{% endhighlight %}

Great, that was easy enough.

Note, I added an [`httparty`](https://github.com/jnunemaker/httparty){:target="_blank"} dependency using `add_runtime_dependency`. This instructs  [`bundle`](http://bundler.io/){:target="_blank"} to install `httparty`, which provides a programmatic Ruby interface to make HTTP requests. However, instead of receiving a response made up of `HTML` which is what you usually get from a server request, I would be looking for JSON<sup id="a4">[4](#JSON)</sup> formatted data which is much easier for a developer to handle in their code.

Now I could start building out my `Kele Class` that would contain all the methods for making `GET` and `POST` requests to Blocs API.

Most importantly, this class, when instantiated as an object, would need to have two key instant variables, accessible for each method.

{% highlight ruby %}
@bloc_api   #Bloc's base API URL: https://www.bloc.io/api/v1
@authenticaition_token #The user's authentication token so requests can be made (the equivalent to being signed in)
{% endhighlight %}

The `@authentication_token` would need to be passed in to every request.

{% highlight ruby %}
class Kele

    include RoadmapMethods

    def initialize(username, password)
        @bloc_api = "https://www.bloc.io/api/v1"
        @authenticaition_token = retrieve_authentication_token(username, password) 
    end

    def retrieve_authentication_token(username, password)
        options = {
            body: {
                email:  username,
                password: password
            }
        }

        response = HTTParty.post("#{@bloc_api}/sessions", options)
        response.ok? ? (response["auth_token"]) : (raise "invalid email or password") 
    end
end
{% endhighlight %}

Given the code above, when the kele object would be created, it would take in a username and password, which should retrieve the authentication token and store it in our instant variable. If this failed, an error would be raised to alert the developer that something had gone wrong. The developer could then rescue and handle this error as they so wished.

On success, the developer would now have an object which, with further methods would be able to seamlessly make requests from Blocs API.
<br/><br/>
<!--    - -->
2\. &nbsp; Arguably not the most challenging task, but it allowed me to start to get to grips with the nature of API requests and the structure of my Ruby Gem for use by other developers.

{% highlight ruby %}
def get_me
    response = HTTParty.get("#{@bloc_api}/users/me", headers: {authorization: @authenticaition_token})
    response.ok? ? (JSON.parse(response.body)) : (raise "Error retrieving current_user")
end
{% endhighlight %}

Remember those Instant Variables that are so crucial to the functioning of our objects methods, here you can see them in action.

I added an instant method to the `Kele Class` that would make a `GET` request using a method that exists on the HTTParty Gem. In that `GET` request I needed to send the `@authenticaition_token` in the header, in order to be allowed access to Blocs API.

If the `response` from Blocs API was successful, I would convert the response body from JSON to a Ruby Hash for ease of use by the developer.

If the `request` was unsuccessful, then I would again make sure to warn the developer by raising an error, which the developer could handle as they wished, perhaps redirecting the user to a different page, or displaying an error message to retry.
<br/><br/>
<!-- - -->
3\. &nbsp; This is not a coding task I hear you cry!

And in truth you would be right. 

However, too often as a developer I have tried to harness the power of other peoples code, whether that be in the form of a Ruby Gem or even a programming framework, only to become disenchanted due to a lack of good, coherent and clear documentation.

In my opinion, it doesn't matter what experience or level of programming a person has obtained, everyone appreciates clear doccumentation and its the backbone of some of the most popular open source projects and naturally the downfall of others.

So here was my attempt at it, writing guidance for the use of the Kele API Client:

># kele <br>
>#### An API Client to access Blocs API<br><br>
>
>Step 1: Open talks with Blocs API
>
>```python
>Kele.new(username, password)
>#returns an object with methods that allow you to talk with Blocs API
>```
><br><br>
>Step 2: Call these great methods **on the returned object** to talk with Blocs API
>
>```python
>.get_me
>#returns current user information
>```
><br>
>```python
>.get_mentor_availability(mentor_id)
>#takes in a mentor_id, this can be found in the user information returned by the get_me method
>#returns the current users mentors availability
>```
><br>
>```python
>.get_roadmap(roadmap_id)
>#takes in a roadmap_id, this can be found in the user information returned by the get_me method
>#returns the current users roadmap information
>```
><br>
>```python
>.get_checkpoint(checkpoint_id)
>#takes in a checkpoint_id, this can be found in the roadmap information returned by the get_roadmap method
>#returns the current users checkpoint information
>```
><br>
>```python
>.get_messages(number = 1)
>#takes in a page number, if no number provided, default will request page 1
>#returns the current users messages
>```
><br>
>```python
>.create_message(sender, recipient_id, subject, body, token = nil)
>#takes in a quite a few arguments
>#sender = email address of the sender
>#recipient_id = id of person you are sending to, id accessible from Bloc API
>#token = a string referenceing a message thread, obtain using .get_messages method. Leave blank to start new thread
>#posts a message to the Bloc API
>```
><br>
>```python
>.create_submission(checkpoint_id, enrollment_id, assignment_branch, assignment_commit_link, comment = "")
>#takes in a quite a few arguments
>#checkpoint_id = integer accessible via get_roadmap method
>#enrollment_id = integer accessible via get_me method
>#assignment_branch = a string, name of assignment branch on git hub
>#assignment_commit_link = a string, link to commit on git hub
>#posts a checkpoint submission to the Bloc API
>```

On top of the need for good documentation, I found this personally a good exercise for me as a developer. It made sure that I knew my code base very well, well enough to explain it to someone approaching it for the first time.

 
<br/><br/>
<!--    - -->
<hr color="gray">



<!-- Results -->

### Results
<!--    - how you tested -->
There was no frontend to manually test against, so I needed to make sure I was able to test thoroughly on the backend. I thought about opting for `RSpec` but given it was a fairly small project, I opted to test the code by using the method calls myself in the `IRB` and using [PRY](https://github.com/pry/pry){:target="_blank"}, specifically `binding.pry` to catch and rectify any bugs. <br>
<!--    - did you get desired outcome -->

I was able to achieve the desired outcomes of the API Client and more importantly I was really able to further my understanding of Ruby Gems, development of open source projects and valuable gems such as `PRY` and `HTTParty`. 
<br/><br/>
<!--    - others reviews -->
Feedback from my codementor was positive.
<hr color="gray">


<!-- Conclusion -->

### Conclusion
<!--    - What were your doubts going into the project? -->
Like I said in the introduction, this was a very interesting project, and I think the biggest doubts I had going in were two-fold. Firstly, there was no frontend, this was pure code and nothing but code, just me and my text editor. Secondly although I never published the gem this would have to be written for others who knew a lot more code than I did, so my code would have to stand up to their scrutiny.
<!--    - What surprised you the most? -->

What surprised me the most from this project was the power of APIs and how they can be used to transmit data between developers, I finally started to grasp why some programmers will build whole applications just using APIs. Moreover, the benefits one can have by creating an API for others to access data from their own site.
<br><br>
<!--    - What would you have done differently? -->
<!--    - What did you learn while doing this project? -->
Although one of the smaller projects at Bloc, I really learnt a lot about writing clean, succinct code and also the value of taking the time out to learn about debuggers such as `PRY` which can save you a lot of time in the future. I was also able to use `PRY` to understand the `HTTParty` gem, as I could look around their code base far quicker and more intuitively using pry commands.

<!--    - How will you use that information in the future? -->
Going forward, this experience of writing an API Client, will help me immensely. Firstly, it made me really get to grips with the generic concept of APIs and how they work. Secondly, it forced me to take even more care of my code, as I was writing it for someone else who was a programmer themselves, and whose own application may depend on the functionality of my Gem. Lastly, it is inevitable that I will now be using `PRY` in not only my Ruby Gem projects, but also in my Ruby on Rails projects.




<br><br><br><br><br><br><br><br><br>
<hr color="gray">
<a name="RG">1</a>: RubyGems is a package manager for the Ruby programming language that provides a standard format for distributing Ruby programs and libraries (in a self-contained format called a "gem"), a tool designed to easily manage the installation of gems, and a server for distributing them.[↩](#a1)

<a name="AC">2</a>: A client library, sometimes called a helper library, is a set of code that application developers can add to their development projects. It provides chunks of code that do the basic things an application needs to do in order to interact with the API.[↩](#a2)

<a name="UserStories">3</a>: A user story is a tool used in Agile software development to capture a description of a software feature from an end-user perspective. The user story describes the type of user, what they want and why. A user story helps to create a simplified description of a requirement.[↩](#a3)

<a name="JSON">4</a>:JSON (JavaScript Object Notation) is a lightweight data-interchange format. It is easy for humans to read and write. It is easy for machines to parse and generate. It is based on a subset of the JavaScript Programming Language, Standard ECMA-262 3rd Edition - December 1999. JSON is a text format that is completely language independent but uses conventions that are familiar to programmers of the C-family of languages, including C, C++, C#, Java, JavaScript, Perl, Python, and many others. These properties make JSON an ideal data-interchange language.[↩](#a4)
