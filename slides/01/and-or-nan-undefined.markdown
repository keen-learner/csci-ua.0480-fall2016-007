---
layout: slides
title: and and or, Checking for Special Values, Style
---
<section markdown="block" class="intro-slide">
# {{ page.title }}

### {{ site.course_number}}-{{ site.course_section }}

</section>
<section markdown="block">
## Inherent Truthiness

__Some quick rules on automatic conversion of strings and numbers to booleans__ &rarr;

* <code>0</code>, <code>NaN</code>, empty string (<code>""</code>), and <code>undefined/null</code> are false
* other values are true-ish

<br>

__Let's test this out...__ &rarr;

<pre><code data-trim contenteditable>
// outputs "in here"
if("this string says false, but...!?") {
	console.log("in here!");
}

// no output
var myString = "";

if(myString) {
	console.log("you shouldn't see me!");
}
</code></pre>

</section>


<section markdown="block">
## And and Or

Some details about <code>&&</code> and <code>||</code>:

* if operands are not actually boolean, convert the value on the left side to a boolean
	* <code>||</code> 
		* will return the __left operand__'s value if it's __true__
		* otherwise, return the value on the right
		* can be used as a way to fall back to a default value <code>potentially_falsey || default_value</code>
	* <code>&&</code> 
		* will return the __left operand__'s value if it's __false__
		* otherwise, return the value on the right
* also... __short-circuit__ evaluation applies
		
</section>

<section markdown="block">
## And and Or Continued

		
Based on the previous slide, __what is the value produced from the following expressions?__ &rarr;

<pre><code data-trim contenteditable>
5 - 5 || 2
5 - 5 && 2
"hello" || "goodbye"
"hello" &&  "goodbye"
</code></pre>

<pre><code data-trim contenteditable>
2
0
hello
goodbye
</code></pre>
{:.fragment}

This actually comes in handy for checking if a property exists on an object, and defaulting to a specific value if it doesn't:
{:.fragment}

<pre><code data-trim contenteditable>
// we haven't seen objects yet, but you get the idea
var obj = {prop1: "a value"}; 
obj.prop1 || "default value"
obj.prop2 || "default value"
</code></pre>
{:.fragment}
</section>

{% comment %}
<section markdown="block">
## null and undefined

Undefined (and also null) means __the absence of a _meaningful_ value__.

However, they're different types!

* <code>undefined</code> is of type <code>undefined</code>
* <code>null</code> is of type <code>object</code>
* !?!?

<pre><code data-trim contenteditable>
console.log(typeof null);
</code></pre>
</section>

<section markdown="block">
## Checking for undefined 


How would you check if a value is __undefined__? __The two ways to do this are__: &rarr;

* {:.fragment} <code>if (typeof myVar == 'undefined')</code>
	* {:.fragment} preferred, handles undeclared variables
* {:.fragment} <code>if (myVar == null)</code>

<br>
(this may be the only time that <code>==</code> would come in handy)
{:.fragment}


</section>
<section markdown="block">
## Checking for NaN

Use the isNaN function to determine if a value is __not a number__.

__(comparing NaN to itself always yields false)__ &rarr;

<pre><code data-trim contenteditable>
NaN == NaN
NaN === NaN

// false
// false
// weird, eh?
</code></pre>
</section>

<section markdown="block">
## Some Style

The previous material in this set of slides are about general best practices. Not adhering to them may:

* result in your code yielding unexpected results
* difficult to understand / non-standard code

<br>
__The next few suggestions, however, are purely stylistic - just about how code is formatted:__ &rarr;

<div markdown="block" class="img">
![poochie](http://i.kinja-img.com/gawker-media/image/upload/s--ZbZrlXcj--/xnfzofkxpckzxbkqxnbq.jpg)
</div>

</section>
<section markdown="block">
## Style Continued

* use 1TBS, __One True Brace Style__: open curly brace on same line of code as last line preceding the current block of code / statement header (not on a new line)
<pre><code data-trim contenteditable>
if (some_boolean_expression) { // <-- curly brace here!
	// do stuff
}
</code></pre>
* use camel case to separate words in identifiers / variables names: <code>myVerboseVariableName</code>
* remember to indent blocks of code!
</section>

<section markdown="block">
## Summary

* use or (<code>||<code>) to check a value and set a default
* to __check for undefined__: <code>if(typeof myVar == 'undefined')</code>
* to __check for NaN__: <code>isNan(myVar)</code>
</section>
{% endcomment %}
