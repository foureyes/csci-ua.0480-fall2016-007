---
layout: slides
title: Functions Addendum
---
<section markdown="block" class="intro-slide">
# {{ page.title }}

### {{ site.course_number}}-{{ site.course_section }}

<p><small></small></p>
</section>

<section markdown="block">
## Topics

* Optional Arguments
* Closures

	
</section>

<section markdown="block">
## Optional Arguments

You can pass as many or as few arguments to functions as you like!

__Wait... what!?__

* if there are two few arguments, those are <code>undefined</code>
* if there are too many, they're ignored
* there's also an <code>arguments</code> variable added to the function's context (along with a this variable) ... maybe we'll check these out later

__Let's check this out__ &rarr;
</section>

<section markdown="block">
## Closure

Functions retain access to their original scope, even when the outer function they were defined in has returned. __What happens here?__ &rarr;

<pre><code data-trim contenteditable>

var gimmeFunction = function() {

	var a = "closure!";

	return function() {
		console.log(a);
	}
}

var myFunction = gimmeFunction();
</code></pre>

closure!
{:.fragment}

</section>
<section markdown="block">
## MakeAdder

Try creating this function:

* takes one argument, a number
* returns a new function that also takes one argument, but returns that argument with the number from the outer function added to it

<pre><code data-trim contenteditable>
var addTwo = makeAdder(2);
console.log(addTwo(5));
// should print out 7
</code></pre>

<pre><code data-trim contenteditable>

var makeAdder = function(x) {
	return function(y) {
		return y + x;
	}
};

var addTwo = makeAdder(2);
console.log(addTwo(5));
</code></pre>
{:.fragment}
</section>
