---
layout: page
title: Contact
permalink: /contact/
feature-img: "img/sample_feature_img_2.png"
---
Please feel free to get in touch.

I would love to hear from you and would be happy to offer any advice and help in any way I can!

You can use the form below or hit the email icon in the top right hand corner of the screen.
<hr color="gray">
<!-- The action attribute defines the action to be performed when the form is submitted. -->
<!-- Normally, the form data is sent to a web page on the server when the user clicks on the submit button. -->
<!-- The form-handler is typically a server page with a script for processing input data. -->
<form action="https://getsimpleform.com/messages?form_api_token=de85fca5406099e946210cda2d92b29f" method="post">
  <!-- the redirect_to is optional, the form will redirect to the referrer on submission -->
  <input type='hidden' name='redirect_to' value='http://samibirnbaum.com/thank-you' />
  <br/><br/>
  <input type='text' name='name' placeholder='Your Full Name' />
  <br/><br/>
  <input type='email' name='email' placeholder='Your E-mail Address' />
  <br/><br/>
  <textarea name='message' placeholder='Write your message ...'></textarea>
  <br/><br/>
  <input type='submit' value='Send Message' />
</form>