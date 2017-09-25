---
layout: post
title: BlocJams
feature-img: "img/sample_feature_img.png"
thumbnail-path: "img/blocjams/blocjams-thumbnail.png"
short-description: A music based application

---

<!-- CASE STUDY HERE -->
<!-- Summary -->
### Summary
<!--    - short and to the point -->
<!--    - starting point >>> outcome -->
My first ever build of an application from scratch.

Welcome to Bloc Jams, a digital music player like Spotify that I built to learn frontend web development.

**This is not supposed to be a  finished product** but was part of the learning process of my web development course with Bloc (CREATE LINK) covering core programming topics.

<!-- my role  -->
### My Role
<!--    - backstory, who and why? -->
To create this application as a sole developer, working remotely, completing specific tasks outlined by Bloc.

<!--    - explanation / relationship you had to the project -->
It was time for me to be thrown into the deep end! Use HTML(5) to build up the content of the application, CSS(3) to style that content for a sleek UI appearance and JavaScript to create attractive dynamic functionality.

Implement two JavaScript libraries: JQuery, and Buzz(LINK) to manage sounds.

Use Git to maintain a local repository of the project and a remote repository on GitHub, and use feature branches to ensure a smooth workflow and secure version control.

Lastly, deploy my application, enhancing my knowledge of Hosting, DNS and Domain Names. 

<!-- Problem -->
### Problems
<!--    - problems you were hired to solve -->
Some of the many ~~problems~~ challenges faced in building this application.

<!--    - -->
1. &nbsp;Refactor standard HTML to meet HTML5 semantic requirements. <br/><br/>
<!--    - -->
2. &nbsp;A neat little feature -  Implement a music player bar that will (eventually with JavaScript 
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;programming) allow users to pause and play songs, view and adjust playback progress, and 
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;adjust volume, using a combination of HTML and CSS.
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;![alt text](../img/blocjams/musicplayerbar.png "Music Player Bar")
<br/><br/>
<!--    - list reasons (before screenshots) -->
3. &nbsp;Achieve Responsive Web Development - ensure that the appplication looks beautiful on all 
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;different size screens from wide screen tv's to laptops to mobiles.
<br/><br/>
<!--    - -->
4. &nbsp;JavaScript/Angular
<br/><br/>
<!--    - -->
5. &nbsp;JavaScript/Angular

<!-- Solution -->
### Solutions
<!--    - -->
1. &nbsp;This was not a challenging task, however, becoming familiar with new doccumentation
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;relating to upgraded web tehnologies is a critical skill in the ever-changing web tech world we 
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;live in.<br/><br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Consequently, I consulted MDN Documentation on HTML5 and refactored the original code. In 
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;this instance changing `<div>` tags to their corresponding HTML5 `<nav>` and `<section>` tags.
<br/><br/>
<!--    - -->
2. &nbsp;In order to break the task down and keep things nice and organised I created three "control 
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;groups":
<br/>
    * Main controls, which contains the play/pause and previous/next buttons.
    * Currently playing, which displays the currently playing song information, including the song 
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; progress.
    * Volume, which contains the volume control slider.
<br/>
{% highlight html %}
<section class="player-bar">
    <div class="container">
        <div class="control-group main-controls">
        </div>
        <div class="control-group currently-playing">
        </div>
        <div class="control-group volume">
        </div>
    </div>
</section> 
{% endhighlight %}
After developing clear and concise HTML I moved on to the CSS creating a user friendly bar using ionicons (LINK).
<br/><br/>
One of the trickier parts was building the song progress and volume bars ("seek bars"):
{% highlight html %}
<div class="seek-bar"> <!--the base transparent progress bar -->
    <div class="fill"></div> <!-- the more opaque colour that fills the seek bar to display progress -->
    <div class="thumb"></div> <!-- the prominent circle at the end of the fill to improve UX -->
</div>
{% endhighlight %}
But using some advanced CSS I was able to achieve the desired look
{% highlight css %}
 .seek-bar {
     height: 0.25rem;
     background-color: rgba(255, 255, 255, 0.3);
     border-radius: 2px;
     position: relative;
     cursor: pointer;
 }
 
 .seek-bar .fill {
     background-color: white;
     width: 36%;
     height: 0.25rem;
     border-radius: 2px;
 }
 
 .seek-bar .thumb {
     position: absolute;
     height: 0.5rem;
     width: 0.5rem;
     background-color: white;
     left: 36%;
     top: 50%;
     margin-left: -0.25rem;
     margin-top: -0.25rem;
     border-radius: 50%;
     cursor: pointer;
     -webkit-transition: all 100ms ease-in-out;
        -moz-transition: all 100ms ease-in-out;
             transition: all 100ms ease-in-out;
 }
 
 .seek-bar:hover .thumb {
     width: 1.1rem;
     height: 1.1rem;
     margin-top: -0.5rem;
     margin-left: -0.5rem;
 }
{% endhighlight %}
Lastly, the music player bar was to remain at the botttom of the users view of the screen at all times. This allowed for easy and smooth control of the music playing, without having to scroll all the way to the bottom of the entire page each time.
<br/><br/>
This was achieved using CSS:
{% highlight css %}
 .player-bar {
     position: fixed; /*explain what each of these did*/
     bottom: 0;
     left: 0;
     right: 0;
     height: 200px;
     background-color: rgba(255, 255, 255, 0.3);
     z-index: 100;
 }
{% endhighlight %}
<!--    - list (after screenshots / code snippers) -->
3\. &nbsp; In order to acheive responsiveness I opted to use media queries. Media queries... 
<br/><br/>
<!--    - -->
4\. &nbsp; JavaScript/Angular
<br/><br/>
<!--    - -->
5\. &nbsp; JavaScript/Angular

<!-- Results -->
### Results
<!--    - how you tested -->
Given this application was only using front-end web technologies. I had two options for testing, either setting up a local server or simply opening my files in the browser itself. I opted for the latter as this met my needs and was quicker to implement.
<br/><br/>
Juidicious use of the DOM within google chromes development tool allowed for thorough testing, catching any mistakes or bugs, fixing and then re-testing again.
<br/><br/>
<!--    - did you get desired outcome -->
I was able to achieve the desired outcomes of the course project. However, given this was only for learning purposes there are naturally things that were not required, which in time i would like to implement or complete.
<br/><br/>
<!--    - others reviews -->
Feedback from my codementor was positive.
<!-- Conclusion -->
### Conclusion
<!--    - What were your doubts going into the project? -->
Going into my first ever project I was excited but naturally I had doubts, I was being thrown into the deep end, being asked to use high-tech skills to problem solve some tricky tasks and ultimatley produce a working application.
<br/><br/>
<!--    - What surprised you the most? -->
What surprised me the most was actually the amount of good, solid, well written code that is needed to produce a high quality application. However, more importantly, how code efficency from the beggining as well as using the right helper libraries can significantly increase efficiency.
<br/><br/>
<!--    - What would you have done differently? -->
<!--    - What did you learn while doing this project? -->
Perhaps one of the most important things i learnt whilst doing this project, beyond the inherent skills themselves, was actually the resources that i could turn to when i felt like i had hit a brick wall.
<br/><br/>
Becoming familar with asking the right questions and communicating with others over slack (LINK) or resoursces like stack overflow (LINK) proved incredibly helpful, when sometimes it takes someone else to see or problem solve from a different angle than you have been pursuing.
<br/><br/>
<!--    - How will you use that information in the future? -->
Going forward, this learning curve, i am sure, will prove its worth, as being able to utilise and engage with the wider coding community can make (almost) any problem, challenge or task achievable.

