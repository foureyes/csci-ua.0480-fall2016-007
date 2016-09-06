---
layout: default
title: Final Project
nav-state: "Final Project"
---
<style>
pre {
	display: inline-block;
	padding: 9.5px;
	margin: 0 0 10px;
	font-size: 15px;
	word-break: break-all;
	word-wrap: break-word;
	background-color: rgb(224, 229, 234);	
	color: #001446;
	border-radius: 4px;
	border: none !important;
}

#final h4 {
	font-size:1.2em;
	margin-top: 1.5em;
	text-decoration: underline;
}
</style>
<div class="panel panel-default">
	<div class="panel-heading">Final Project</div>
	<div class="panel-body" markdown="block">

# __Final Project, Due Sun, May 8th at 11pm__

(extended from May 6th)

## Overview 

Create a web application using Express and MongoDB.

<a name="requirements">

## Project Requirements

* Write project documentation / specifications
* Use Express and MongoDB (or other database with permission)
* Have at least __5 route handers__ (do not count login/register gets and posts if you're implementing auth)
* Have _around_ __4 Mongoose Schemas__  (or other database abstraction library/module)
* Have at least 3 forms (do not count login/register gets and posts if you're implementing auth): 
	* Minimally, __one of the forms must submit data using JavaScript (ajax)__
	* Ensure that __server side validation occurs__
	* Additionally, __validation errors should be propagated back to the front end__
* Use at least 2 of any of the following (can be the same): Constructors, Object.create, Prototypes, map, reduce, filter, forEach
* __Additional Research Requirements__ (see below)
* Project deployment
* __Do not allow user generated content to be displayed directly (allow the default handlebars behavior that converts HTML entities)__


## Additional Requirements, Your Choice

Choose at least __6 points__ worth of these following topics (research and implementation). __This list may change slightly (added items, adjustments to points) as project ideas come in.__ 

* (2 points) Unit testing with JavaScript
	* [Jasmine](http://jasmine.github.io/)
	* [Mocha](https://github.com/mochajs/mocha)
	* Any others found through research
    * (You'll have to specify how to run tests or show screen capture of tests)
* (3 points) Automated functional testing for all of your routes using any of the following:
	* [PhantomJS](http://phantomjs.org/) - headless browser testing
	* [Selenium](http://www.seleniumhq.org/)
	* Any others found through research
    * (You'll have to specify how to run tests or show screen capture of tests)
* (2 points) Configuration management
	* [nconf](https://github.com/flatiron/nconf)
	* [Node convict](https://github.com/mozilla/node-convict)
	* Any others found through research
* (1 point) Use [grunt](http://gruntjs.com/), [gulp](http://gulpjs.com/), or even make (!) to automate any of the following ... must be used in combination with one or more of the other requirements, such as:
    * (1 point) Integrate JSHint / JSLint into your workflow
        * Must be used __with build tool__ (see above requirement on Grunt or Gulp
        * Must have have .jshint configuration file
        * Must run on entire codebase __outside of <code>node_modules</code>
    * (1 point) Concatenation and minification of CSS  and JavaScript files
        * Must be used __with build tool__ (see above requirement on Grunt or Gulp
        * (Only client side files!)
    * (1 points) Use a CSS preprocesser
	    * [Sass](http://sass-lang.com/)
	    * [Less](http://lesscss.org/)
	    * [Myth](http://www.myth.io/)
* (3 points) Integrate user authentication
	* Minimally, implement sign up and registration
	* Or implement sign in with provider, such as FB Connect, Google, etc. (which could be worth more points)
* (3 points) Use a different database and database abstraction layer (!)
* (2 points) Perform client side form validation using a JavaScript __library__
    * using html5 form elements with attributes as contraints does not count
    * alerting errors also does not count; errors must be integrated into the DOM
* (1 point) Use a CSS framework throughout your site, use a reasonable of customization of the framework (don't just use stock Bootstrap - minimally configure a theme):
	* [Bootstrap](http://getbootstrap.com/)
	* [Foundation](http://foundation.zurb.com/)
* (1 point) Use a __server-side__ JavaScript library or module that we did not cover in class (not including any from other requirements) - 1 point per library, maximum of 2
* (1 point) Use a __client-side__ JavaScript library or module that we did not cover in class (not including any from other requirements) - 1 point per library, maximum of 2
* (2 points) Per external API used (you can convince me that this is worth more points for a more complex API)

<a name="milestone1"></a>

## Milestones

<a name="proposal"></a>

### __4/5__ - Milestone 1 - Requirements / Specifications and Data Model 

[Check out sample documentation](https://github.com/nyu-csci-ua-0480-010-spring-2016/jversoza-final-project)

* Documentation
	* Submit electronically through a supplied GitHub repository
	* Write everything up in your README.md
		* Drop the images into your repository (either under a separate branch or in a folder called documentation)
		* [Link to it based on this SO article](http://stackoverflow.com/questions/10189356/how-to-add-screenshot-to-readmes-in-github-repository)
	* A one-paragraph description of your project
	* Requirements
		* Sample documents (JSON / JavaScript literal objects will be fine, or your actualy Schemas) that you will store in your database, and a description of what each document represents
		* Enumerate any references from one document to another
	* Wireframes ([like this one](http://upload.wikimedia.org/wikipedia/commons/4/47/Profilewireframe.png)) 
		* [a great article on wireframes](http://www.onextrapixel.com/2011/03/28/creating-web-design-wireframes-tools-resources-and-best-practices/)
		* some possible tools
			* Hand-drawn
			* Balsamiq
			* Google drawings
			* Omnigraffle
			* Adobe tools such Photoshop (psds), Illustrator (ai) etc.
	* [A Site Map (see examples)](http://creately.com/diagram-community/popular/t/site-map)
	* One of the following to represent what your application will actually do:
		* A list of user stories ([simply a list of sentences in the form of _as a &lt;type of user&gt;, I want &lt;some goal&gt; so that &lt;some reason&gt;_](http://en.wikipedia.org/wiki/User_story#Format))
		* A list/spreadsheet of [use cases (see the end of this article)](http://www.stellman-greene.com/2009/05/03/requirements-101-user-stories-vs-use-cases/)
		* A [Use Case Diagram](https://www.andrew.cmu.edu/course/90-754/umlucdfaq.html)
	* __Which modules / concept will you research?__
		* List of research topics
		* A brief description of concept (3 or 4 sentence each)
			* What is it?
			* Any theoretical underpinnings worth mentioning?
			* Why use it?
			* List of possible candidate modules or solutions
* Code
	* A skeleton express app
		* Start populating your package.json with required modules
	* A 1st draft mongoose schema

<div id="final" markdown="block">

<a name="milestone2">

<br>
<br>
<br>

### Date 4/22 - Milestone 2 - Prototype With Some Implemented Functionality (10 points total)

1. (4 points) create at least 1 form that can add data to your database
2. (3 points) have at least 1 page that reads data from your database
3. (3 points) partially implement one of your research topics
4. create a markdown file called <code>milestone02.md</code>
    * specify the url that shows your form (for example, <code>http://localhost:3000/pizzas</code>)
    * specify the url that shows a page reading data
    * specify the url or directory for your research topic
5. make sure that you have a <code>package.json</code> with all of your project's required dependencies so that numbers 1 through 3 will function
6. __after pushing your code to github__:
    * clone your project in a different directory
    * run <code>npm install</code> and <code>nodemon bin/www</code> 
    * and verify that your project works
    * (if your project is not _runnable_, you will not receive credit for this milestone)

{% comment %} 
* 1 or more forms and their corresponding route handlers
* Demonstrate that at least 2 route handlers can read and write from MongoDB
* Proof of concepts for some of your research topics (for example, if you wanted to use sass, I'd expect that you've made some progress integrating it into your project)
* Prep for deploying your project
    * Directions to be added for deploy prep
    To prep for deploying your app so that it's accessible online... retrieve your password for the cs department's server for undergraduate students (i6)  and ensure that you can log in:
	1. Get the new password that you'll use to log in to i6 by going to https://cims.nyu.edu/webapps/password ...and entering your netid and password
	2. Use the i6 password that you received to log in to a remote server using the commandline tool, ssh (substituting your lowercase net id for your_net_id): <code>ssh your_net_id@i6.cims.nyu.edu</code>
	3. If you're unable to do this, please email me!
* (If you're not using the technologies above, use your best judgement to determine what's an appropriate amount of progress)
* Lastly, bring your laptop to class on Tuesday, the 24th so that we can try deploying a test node application!!! (and potentially deploying your prototype!)
{% endcomment %} 

<br>
<br>
<br>
<br>

<a name="milestone3">

### 5/3 - Milestone 3 - Refined Prototype and Attempt to Deploy

1. attempt to deploy your code to i6 by following [these instructions](homework/deploy.html)
2. use [this form to send me the urls](https://docs.google.com/a/nyu.edu/forms/d/112J7_jnQFozXiLUtHdRIxcCFnEomEMdCYbnNLX5AyrQ/viewform) of: 
    * two working forms in your __deployed__ application 
        * they should allow data to be modified or deleted
        * the results of these forms should be apparent/viewable
    * show progress on at least 2 of your research topics; the url that shows you've implemented what you've researched can be:
        * a page on your site that's deployed to i6
        * a link to the github repository / line no
3. I can augment my office hours on Monday if you need help with deployment
    * (really, deployment will be the bulk of your _work_ ... if you completed the previous milestone, then there will be little work for you to do to complete #2)
    * send me an email if you're having issues with deploying

<br>
<br>
<br>
<br>


<a name="milestone5">

### __5/8__ - Final Project Complete - Code is  _Deployed_ 

* __(extended from Fri, 5/6 to Sun, 5/8)__ to allow some time over the weekend to finish up project
* late submissions accepted within __24 (Mon, 5/9) hours with 10% penalty__ applied to this last milestone (regardless of previous lates)
* day after final exam submissions accepted with significant penalty (-25% of total possible points) upon email request
* after that, no submissions will be accepted

<br>
<br>
<br>

<a name="suggestions">

{% comment %}
## Potential Projects

* A project portfolio site
* Create a one-player game with a computer AI - allow logins, saved high scores, saved games
	* Maybe something like Cookie Clicker ...
	* or a Battleship clone
* Or... whatever you can come up with!
{% endcomment %}
</div>
</div>
</div> 
