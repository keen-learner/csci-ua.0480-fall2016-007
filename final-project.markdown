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

# __Final Project, Due__ <strike>Saturday, Dec 3rd at 11pm</strike> __Monday, Dec 12th at 11pm____

## Overview 

Create a web application using Express and MongoDB.

<a name="requirements">

## Project Requirements

### Requirements

* You must use Express and MongoDB (or other server-side framework and database with permission)
* You must write your own code, with annotations/references added for any code sourced from books, online tutorials, etc.

### Scoring Rubric

* (30 points) minimum 3 x forms or ajax interactions (__excluding login__)
* (9 points) minimum 3 x any of the following (can be the same): 
    * original Constructors (that is, a constructor you've written yourself), including methods added to prototype
    * Object.create (where prototype matters)
    * es6 classes 
    * original higher order functions or these built-in higher order functions on the Array object: map, reduce, filter
* (8 points) minimum 2 x mongoose schemas
* (10 points) stability / security
    * simple validation on user input to prevent application from crashing
    * doesn't allow user input to be displayed unescaped directly on page
    * pages that require authentication cannot be accessed without authentication
    * data specified as private to a user cannot be viewed by another user
    * etc.
* (5 points) _originality_ 
    * is not mostly based on existing homework
    * majority of code is not from online tutorial
* (30 points) 3 x milestones: 
    * requirements and model
    * deploy and partial implementation
    * nearly finished
* (8 points) worth of research topics; see below


{% comment %}
* provide api end points
* what data is authenticated
* urls of where data
{% endcomment %}

## Additional Requirements, Your Choice

Choose at least __8 points__ worth of these following topics (research and implementation). __This list may change slightly (added items, adjustments to points) as project ideas come in.__ 

* (4 points) Unit testing with JavaScript
	* [Jasmine](http://jasmine.github.io/)
	* [Mocha](https://github.com/mochajs/mocha)
	* Any others found through research
    * Minimally 4 tests
    * You'll have to link to testing code in repository
    * ... And either specify how to run tests or show screen capture of tests)
* (6 points) Automated functional testing for all of your routes using any of the following:
	* [PhantomJS](http://phantomjs.org/) - headless browser testing
	* [Selenium](http://www.seleniumhq.org/)
    * Minimally 4 tests
    * You'll have to linke to testing code in repository
	* Any others found through research
    * You'll have to link to testing code in repository
    * ... And either specify how to run tests or show screen capture of tests)
* (4 points) Configuration management
	* [nconf](https://github.com/flatiron/nconf)
	* [Node convict](https://github.com/mozilla/node-convict)
	* Any others found through research
* (4 points) Use [grunt](http://gruntjs.com/), [gulp](http://gulpjs.com/), webpack or even make (!) to automate any of the following ... must be used in combination with one or more of the other requirements, such as:
    * (2 points) Integrate JSHint / JSLint into your workflow
        * Must be used __with build tool__ (see above requirement on Grunt or Gulp
        * Must have have .jshint configuration file
        * Must run on entire codebase __outside of <code>node_modules</code>
    * (2 points) Concatenation and minification of CSS  and JavaScript files
        * Must be used __with build tool__ (see above requirement on Grunt or Gulp
        * (Only client side files!)
    * (2 points) Use a CSS preprocesser
	    * [Sass](http://sass-lang.com/)
	    * [Less](http://lesscss.org/)
	    * [Myth](http://www.myth.io/)
* (6 points) Integrate user authentication
	* Minimally, implement sign up and registration
	* Or implement sign in with provider, such as FB Connect, Google, etc. (which could be worth more points)
* (4 points) Perform client side form validation using custom JavaScript or JavaScript __library__
    * errors must be integrated into the DOM 
    * the following will not receive full credit:
        * using form elements with attributes as constraints 
        * displaying errors with `alert`
* (2 points) Use a CSS framework throughout your site, use a reasonable of customization of the framework (don't just use stock Bootstrap - minimally configure a theme):
	* [Bootstrap](http://getbootstrap.com/)
	* [Foundation](http://foundation.zurb.com/)
* (1 - 6 points) Use a __server-side__ JavaScript library or module that we did not cover in class (not including any from other requirements) 
    * assign a point value to the library or module that you're using based on amount of effort and/or code required for integration
* (1 - 6 points) Use a __client-side__ JavaScript library or module that we did not cover in class (not including any from other requirements)
    * assign a point value to the library or module that you're using based on amount of effort and/or code required for integration
    * for example, angular 2 or d3 might be 6 points, while google maps might be 1 point
* (1 - 6 points) Per external API used 
    * assign a point value to the library or module that you're using based on amount of effort and/or code required for integration
    * for example, angular 2 might be 6 points, while google maps might be 1 point

<a name="milestone1"></a>

## Milestones

<a name="proposal"></a>

### __11/7__ - Milestone 1 - Requirements / Specifications and Data Model (10 points)

[Check out sample documentation](https://github.com/nyu-csci-ua-0480-001-fall-2016/final-project-example)

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
			* Why use it?
			* List of possible candidate modules or solutions
            * Points for research topic (based on specifications above)
* Code
	* A skeleton express app
		* Start populating your package.json with required modules
	* A 1st draft mongoose schema

<div id="final" markdown="block">

<a name="milestone2">

<br>
<br>
<br>

### 11/16 - Milestone 2 - Initial Deployment and First Form (10 points)

1. attempt to deploy your code to i6 by following [these instructions](homework/deploy.html)
2. use [this form to submit urls to your deployed site](https://docs.google.com/a/nyu.edu/forms/d/e/1FAIpQLSfNVdjXefEJRdx_NmC26VI6GJfj_ezcnwB2UHR4C9C8nDJPVA/viewform)
3. your deployed site should contain the following progress:
    * __one working form (that is not login or registration)__ 
        * ...that should allow data to be modified or deleted
        * the results of submitting this form should be apparent/viewable
    * show progress on at least 1 of your research topics; the url that shows you've implemented what you've researched can be:
        * a page on your site that's deployed to i6
        * a link to the github repository / line no


<a name="milestone3">

<br>
<br>
<br>

### 12/2 - Milestone 3 - 2nd Form and More Progress on Research(10 points)

1. make at least 3 additional commits to add:
    * your 2nd form / ajax interaction
    * make more progress on your research topics
2. redeploy your code to i6 by running git pull and restarting forever
    1. `ssh` into i6
    2. `cd` into your project directory (should be in `~/opt/NETID-final-project`)
    3. run `forever stopall` and `forever start bin/www` 
        * __YOU MUST MAKE SURE THIS IS WORKING AFTER DECEMBER 1ST DUE TO SCHEDULED DOWNTIME FOR SERVERS__
        * you'll have to use the full path to forever, likely `~/usr/local/node_modules/bin/forever`
        * and perhaps the full bath to `bin/www`
3. use [this form to submit urls for the following](https://docs.google.com/a/nyu.edu/forms/d/e/1FAIpQLSdZamAL1MURfHInQPWjLjcs0xB__QOyjiwl1J_YNROJD8c5gg/viewform)
    * __both working forms or ajax interactions (that are not login or registration)__ 
    * a link to show code changes since milestone #2:
        * start with the url to your repository: `https://github.com/nyu-csci-ua-0480-001-fall-2016/NETID-final-project/`
        * and append the following to the url: `compare/master@%7B11-18-16%7D...master`
        * for example: `https://github.com/nyu-csci-ua-0480-001-fall-2016/NETID-final-project/compare/master@%7B11-18-16%7D...master`


<a name="final_submit">

<br>
<br>
<br>
<br>


### __12/12 11PM__ - Final Project Complete and Code is fully  _Deployed_ 

* __all commits must be in by Monday, December 12th__
* any late commits will result in point deductions: 10% off of grade
* __project must be deployed__ on i6 (or other platform, such as Heroku, gomix, zeit, etc.)
    * if your application needs to be restarted while being graded; I will contact you
    * you will not receive a penalty for restarting after the due date
* __the [final project form submission](https://docs.google.com/a/nyu.edu/forms/d/e/1FAIpQLSe0OP9NvaBPX1quV-bOU3_WmOTt-Yk-sAxkTLBrWm5VP_pyzw/viewform) must be filled out__ (if a form is not submitted, you will receive a 0 for your project)
    * late project form submission will also result in a small point deduction

</div>
</div>
</div> 
