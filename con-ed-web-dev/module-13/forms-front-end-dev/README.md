# Forms

Forms make up an important part of front-end development and are used to take in information from users. This includes sign-in forms, search bars and any other type of user interaction.

Simply put, forms are everywhere! They have their own unique set of HTML elements and attributes, and require specific CSS to help style them.


## Forms and front-end development

At their base, forms are a collection of *inputs* that take in user information.  

For example, below is a common form that social media users are used to seeing - the Medium login page. 

![Medium login page](https://hychalknotes.s3.amazonaws.com/medium-form--conEd.png)

It is a form that asks users to sign in using an email. 

The form is made up of:
* A _label_ which says "Your email". This provides direction to users.
* An input for users to write their email address.
* A _submit button_ that sends the inputted information to the server.

This is all done in the browser and completed on the _front end_. The front end is the section of an application or website that a user directly interacts with. This is also referred to as _client-side_ processing, since the "client" is the user and the processing happens in their browser, on their machine.

Once submitted, the form information is sent to Medium's server where the information is verified. If the information provided is correct, the user will be successfully registered or logged into their account; if it isn't, they will get an error message. All this is all done on the _back end_ (also referred to as _server-side_ processing). 

Currently, HTML and CSS cannot extensively verify or store information, which is why server side languages take care of that for us. Server side languages can also:

* Check if username and password match
* Store an uploaded photo
* Post a new listing, article, blog post etc.
* Add a comment on a blog post, article, etc.
* Post a tweet, status update, story, and/or otherwise update a user's social media timeline

We won't be touching on any server side languages in this course, but if you do want to explore what happens once you submit a form to a server, you can look into learning a language such as Ruby (Ruby on Rails framework), PHP (Code Igniter/WordPress), Python (Django), NodeJS (JavaScript on the server), ASP /.NET ( Microsoft products).

Lucky for front-end developers like us, there are services that do the entire server-side part for us. A service such as [https://formspree.io/](https://formspree.io/) can help us send the data from our forms to a specified email. (Note that Formspree will only work if your site is live.)
