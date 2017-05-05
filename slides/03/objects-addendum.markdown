---
layout: slides
title: Objects Addendum
---
<section markdown="block" class="intro-slide">
# {{ page.title }}

### {{ site.course_number}}-{{ site.course_section }}

<p><small></small></p>
</section>
<section markdown="block">
## Objects and Mutability

* numbers, strings and booleans are all immutable! 
* objects are not - they can be changed!
* (for example - assignment)
* arrays are objects; they're mutable too!
* __we can try reversing an array two ways... return a new array or mutate the existing one__ &rarr;
</section>
<section markdown="block">
## Mutability and References

__What will this print out?__ &rarr;
<pre><code data-trim contenteditable>
a = [1, 2, 3];
b = a;
b.push(4);
console.log(a, b);
</code></pre>

<pre><code data-trim contenteditable>
[ 1, 2, 3, 4 ] [ 1, 2, 3, 4 ]
</code></pre>
{:.fragment}

(We can use the slice method to copy an Array instead of _aliasing_: <code>a.slice()</code>) 
{:.fragment}
</section>

<section markdown="block">
## Arguments Object

When a function is called, it gets an __arguments__ in its context, along with its defined parameters (and __this__, but we'll talk about that later).


<pre><code data-trim contenteditable>
var f = function() {
    // btw... ok - I get the funny coercion rules now
    console.log("number of args " + arguments.length);
    for (var i = 0, j = arguments.length; i < j; i++) {
        console.log(arguments[i]);
    }
};
f(1, 2, 3);

</code></pre>

</section>

<section markdown="block">
## Arguments Object Continued

* Array like, but not an Array (__let's see__ &rarr;)
* you can index into it
* you can get it's length
* you can loop over it
* no methods, like slice
* how might you do required and optional arguments?
* {:.fragment} loop over arguments, but start at appropriate index

</section>
