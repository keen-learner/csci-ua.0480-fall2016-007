---
layout: slides
title: Review Functions
---
<section markdown="block" class="intro-slide">
# {{ page.title }}

### {{ site.course_number}}-{{ site.course_section }}

<p><small></small></p>
</section>

<section markdown="block">
## Converting Types

JavaScript has a bunch of rules when it comes to automatic conversion.

__Get around them by:__  &rarr;

* always using === ... 
* converting things yourself
{:.fragment}
</section>

<section markdown="block">
## Converting Types Continued

__So... uh... how do I get from one type to another?__ &rarr;

* !!5
* 5 + ""
* +"5"
* also constructors
* also parseInt with radix
{:.fragment}

</section>


<section markdown="block">
## Scope

__What's the only way to create scope in JavaScript?__ &rarr;

* the only way to create scope in javascript is with functions!
* closest enclosing scope first 
{:.fragment}
</section>

<section markdown="block">
## Function Declaration

__What's the difference between these two ways of creating functions...__ &rarr;

<pre><code data-trim contenteditable>
function f() {}

var f = function() {};
</code></pre>

The function declaration (the first one) is hoisted.
{:.fragment}
</section>

<section markdown="block">
## Some Rules

Lastly... 

* always end statements with a semicolon
* always declare your variables (use <code>var</code>)
* don't declare functions in non-function block (such as an if statement)
</section>
