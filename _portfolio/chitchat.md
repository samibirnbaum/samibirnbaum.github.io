---
layout: post
title: Chit Chat
feature-img: "img/sample_feature_img.png"
thumbnail-path: "img/projects/chitchat/chitchat.png"
short-description: Creating a chat room

---

[Source Code on Git Hub](https://github.com/samibirnbaum/chitchat){:target="_blank"}
<hr color="gray">


<!-- CASE STUDY HERE -->
<!-- Summary -->
### Summary
<!--    - short and to the point -->
<!--    - starting point >>> outcome -->
A frontend chat room 'style' application.

Welcome to Chit Chat, an application that sends and receives messages in real time using [Firebase](https://firebase.google.com/){:target="_blank"} and AngularJS.

<!--tech used-->
##### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Spec:
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; HTML(5) <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; CSS(3) <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; [UI Bootstrap](http://angular-ui.github.io/bootstrap/versioned-docs/2.5.0/#!#top){:target="_blank"}<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; JavaScript <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; AngularJS <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; [Firebase](https://firebase.google.com/){:target="_blank"}<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; [AngularFire API](https://github.com/firebase/angularfire){:target="_blank"}<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Git & Git Hub

**This is not supposed to be a  finished product** but was part of the learning process of my web development course with [Bloc](https://www.bloc.io/){:target="_blank"} covering core programming topics.
<hr color="gray">



<!-- my role  -->
### My Role
<!--    - backstory, who and why? -->
To create this application as a sole developer, working remotely, completing specific tasks outlined by Bloc.

<!--    - explanation / relationship you had to the project -->
I was provided with User Stories <sup id="a1">[1](#UserStories)</sup> that I had to comprehend and complete.
* As a user, I want to see a list of available chat rooms
* As a user, I want to create chat rooms	
* As a user, I want to see a list of messages in each chat room	
* As a user, I want to set my username to display in chat rooms	
* As a user, I want to send messages associated with my username in a chat room

After studying the user stories, I was able to sketch out some wireframes<sup id="a2">[2](#Wireframes)</sup> of the overall vision I had for the look of the application.

I used Git to maintain a local repository of the project and a remote repository on GitHub, and used feature branches to ensure a smooth workflow and secure version control.
<hr color="gray">


<!-- Problems -->

### Problems
<!--    - problems you were hired to solve -->
Naturally, there were numerous challenges throughout this project, including ~~infuriating~~ rewarding debugging sessions. Whilst impossible to list them all, I will document a few to give you an idea of some of the problems I faced and how I set about solving them.

<!-- list 3 -->
1. &nbsp; The user would like to see a list of available chat rooms when they visit the site, can I query 
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;these chat rooms from Firebase and display them on the frontend to the user?<br/><br/>
<!--    - -->
2. &nbsp;Initiate a modal on the frontend, using [UI Bootstrap](http://angular-ui.github.io/bootstrap/versioned-docs/2.5.0/#!#top){:target="_blank"}, for a user to create a new chat room. <br><br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;![alt text](../img/projects/chitchat/modal2.png "Modal")
<br/><br/>
<!----->
3. &nbsp;Efficiently store a users username so you can display it every time they visit the site and write something in a chat room.<br/><br/>
<hr color="gray">


<!-- Solutions -->

### Solutions
<!--    - -->
1. &nbsp;In my opinion the crux of this problem was the querying of Firebase. I felt that once I had that in place, to actually display the information on the frontend would be relatively straightforward.

In order to thoroughly test whether I was making a successful query from Firebase, I manually added some rooms to the Firebase database. (At a later stage the user would be adding these rooms via the frontend). 

The data structure looked like this:

```
bloc-chat-1482f
|__rooms
    |__1:"room1"
    |__2:"room2"
    |__3:"room3"
```
With this out the way I was ready to start building my query.

I created a `Room` factory in Angular that would define all Room-related API queries. I created a reference to my Firebase database inside, and injected the [`$firebaseArray`](https://github.com/firebase/angularfire/blob/master/docs/reference.md#firebasearray){:target="_blank"} service provided by AngularFire: 

{% highlight javascript %}
  function Room($firebaseArray) {
    var Room = {};
    var ref = firebase.database().ref().child("rooms");
    var rooms = $firebaseArray(ref);

    Room.all = rooms;

    return Room;
  }
{% endhighlight %}

Using the `$firebaseArray` service ensured the data returned would be an array and therefore easier to manipulate using JavaScript.

The `Room` factory within my application:

{% highlight javascript %}
(function() {
  function Room($firebaseArray) {
    var Room = {};
    var ref = firebase.database().ref().child("rooms");
    var rooms = $firebaseArray(ref);

    Room.all = rooms;

    return Room;
  }

  angular
    .module('blocChat')
    .factory('Room', ['$firebaseArray', Room]);
})();
{% endhighlight %}

Now I was able to query the rooms I went on to create a template and controller to display the rooms to the user.

<br/>
<!--    - -->
2\. &nbsp;Initially, this seemed like one of the more straightforward tasks of the whole project. After all I've used bootstrap before, but it turned out to be far from it! (welcome to web development).

This one left me stumped for days.

I trawled through the doccumentation time and time again, attempted to use every resource I had at my disposal but for one reason or another I couldn't get my modal to work.

I would later understand that the reason I found this so difficult was because I didn't know what a JavaScript `promise` was and once this concept was understood, that filled in (nearly) all the missing gaps.

However, at the time, I reached out to a code mentor on the course and together we pair-programmed to get the modal up and running.

The reason I wanted to write about this, is because this actually became a really helpful learning curve for me in the end (but more on that later in the conclusion).

The generic steps I did take to get this done were:
* I included the `UI Bootstrap` library via a `<script>` tag on `index.html`.
* I injected the module into my Angular app's dependency array
* I created a separate controller for the modal
* I injected the proper dependencies for using the modal (see the [UI Bootstrap documentation](http://angular-ui.github.io/bootstrap/versioned-docs/2.5.0/#!#modal){:target="_blank"})
* I added methods to open, close and submit data to Firebase from the modal
<br/><br/>
<!-- - -->
3\. &nbsp;My approach to this was to store the username on the clients browser using cookies (insert token joke about cookies).

This is by far not the only approach and arguably not the best. In my Ruby on Rails applications I store this type of data in the database and utilise browser sessions with users signing in.

However, this was part of learning and getting to grips with cookies and how they _can_ be used to good affect.

Thankfully, Angular has an external module for including the services and methods associated with cookies.

Most importantly, I would have to be able to check if the user had a cookie which included a current username, if they did, I would use that username, if not I would need to prompt them to enter a username and create a cookie to store that in. Welcome back to the dreaded modal:

{% highlight javascript %}
(function(){

    function BlocChatCookies($cookies, $uibModal){ //this function will fire when angular app runs (user opens site)
        var currentUser = $cookies.get('blocChatCurrentUser'); //returns the value of this cookie key
        if(!currentUser||currentUser===""){ 
            var modalInstanceObject = $uibModal.open({
                animation: false,
                keyboard: false,
                templateUrl: '/templates/usernameModalInstance.html',
                controller: 'UsernameModalInstanceCtrl',
                controllerAs: 'UsernameModalInstance'
            });

            modalInstanceObject.result.then(function(username){
                $cookies.put("blocChatCurrentUser", username);
            });
        }
    }

    angular
        .module("blocChat")
        .run(["$cookies", "$uibModal", BlocChatCookies]); //on the ngCookies module there is a $cookies service to help us interact with cookies

})()
{% endhighlight %}
<br/><br/>
<!--    - -->
<hr color="gray">



<!-- Results -->

### Results
<!--    - how you tested -->
Given the frontend nature of the project I was able to test thoroughly using the browser, chrome dev tools and the DOM.
<!--    - did you get desired outcome -->

I was able to achieve the desired outcomes of the course project. However, given this was only for learning purposes there are naturally things that were not required, which for production purposes would need to be implemented.
<br/><br/>
<!--    - others reviews -->
Feedback from my code mentor was positive.
<hr color="gray">


<!-- Conclusion -->

### Conclusion
<!--    - What were your doubts going into the project? -->
This was the final frontend project with [Bloc](https://www.bloc.io/){:target="_blank"} and with this in mind I was given very little support to complete the tasks at hand and was challenged to draw on my own initiative and external resources.
<!--    - What surprised you the most? -->

What surprised me the most whilst working through this project was the rigidity of the framework AngularJS. In full honesty I did not find the framework to be intuitive and although it ships with some great features, as a beginner user I would be less inclined to pursue a project using Angular.

This has, however, given me the desire to learn a different framework called [React](https://reactjs.org/){:target="_blank"} which thankfully is becoming very popular and I have access to great learning materials through [Bloc](https://www.bloc.io/){:target="_blank"}. Hopefully, in the near future I can add this to my skill set and I will find React to be far more efficient and user friendly.
<!--    - What would you have done differently? -->

<!--    - What did you learn while doing this project? -->
The biggest learning curve for me on this whole project was hitting a brick wall. I must have spent days trying to get [UI Bootstraps](http://angular-ui.github.io/bootstrap/versioned-docs/2.5.0/#!#top){:target="_blank"} modal to work on my site and shouting at inanimate objects (such as my pc) were becoming common place. However, what I did learn, was that it's really important to reach out to others and sometimes problem-solving with someone else can help you to learn someting new or see something from a different angle. In this instance the code mentor introduced me to a new concept in JavaScript `promises`, and I would definetly collaborate far quicker in the future. 

<!--    - How will you use that information in the future? -->
Moving forward, I would like to learn React in the future, especially as I have access to the learning material through my Bloc curriculum. And even though I do work remotely I think that I would be far more inclined to pair-programme with others to enhance collaboration and problem-solving.

<br><br><br><br><br><br><br>
<hr color="gray">
<a name="UserStories">1</a>: A user story is a tool used in Agile software development to capture a description of a software feature from an end-user perspective. The user story describes the type of user, what they want and why. A user story helps to create a simplified description of a requirement.[↩](#a1)

<a name="Wireframes">2</a>: Wireframing is a way to design a website service at the structural level. A wireframe is commonly used to lay out content and functionality on a page which takes into account user needs and user journeys. Wireframes are used early in the development process to establish the basic structure of a page before visual design and content is added.[↩](#a2)



<!-- Code Blocks: -->
{% highlight html %}
{% endhighlight %}
{% highlight css %}
{% endhighlight %}
{% highlight javascript %}
{% endhighlight %}
