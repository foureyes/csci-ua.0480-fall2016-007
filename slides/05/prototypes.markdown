---
layout: slides
title: "Prototypes"
---
<section markdown="block" class="intro-slide">
# {{ page.title }}

### {{ site.course_number}}-{{ site.course_section }}

<p><small></small></p>
</section>
<section markdown="block">
## Where did we Leave Off?

At a cliffhanger! 

<br>
(Actually... doing some magic tricks)
{:.fragment}
</section>


<section markdown="block">
## Pulling Properties Out of Thin Air!

__Let's check out this code.__ &rarr;

<pre><code data-trim contenteditable>
// an empty object
var hat = {}; 

// printing out a properties
console.log(hat.toString);

// calling a method
console.log(hat.toString());
</code></pre>

* __Have we defined any properties on the object, <code>hat</code>, yet?__ &arr;
* __What do we expect the output to be?__ &rarr;

<pre><code data-trim contenteditable>
[function: toString]
[object object]
</code></pre>
{:.fragment}

</section>

<section markdown="block">
## So Where Did Those Properties Come From?

<pre><code data-trim contenteditable>
var hat = {}; 
console.log(hat.toString); // a function
console.log(hat.toString()); // returns object
</code></pre>

<div markdown="block" class="img">
![rabbit out of a hat]({{ site.slides_img_prefix }}/rabbit-hat.gif)
</div>
</section>

<section markdown="block">
## Inherited Properties

__All objects have a link to another object that's called its <code>prototype</code>__.

* objects are basically just a collection of properties
* when an objects gets a request for a property that it doesn't have, the object's prototype is searched for that property
* <code>prototype</code> objects have prototypes as well!
* the search for a property goes on up the chain of prototypes until
	* the property is found
	* an object with a <code>null</code> prototype is reached / the last object in the chain: <code>Object.prototype</code>
</section>

<section markdown="block">
## Object.prototype

The top level prototype is [Object.prototype](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/prototype):

* all objects in JavaScript are descended from <code>Object</code>
* all objects inherit methods and properties from <code>Object.prototype</code>
* __<code>Object.prototype</code>'s prototype is <code>null</code>__

<br>
__Let's do some exploring.__ &rarr;

* use <code>Object.getPrototypeOf(obj)</code> 
* this gives back the prototype of the passed in object <code>obj</code>... 

<pre><code data-trim contenteditable>
console.log(
	Object.getPrototypeOf({}) == Object.prototype);

console.log(
	Object.getPrototypeOf(Object.prototype)); 
</code></pre>
{:.fragment}

</section>

<section markdown="block">
## Object.prototype Continued

<code>Object.prototype</code> isn't always an object's direct prototype; instead, most objects have a prototype of another object

* __functions__ derive from <code>Function.prototype</code>
* __arrays__ derive from <code>Array.prototype</code>

<br>
__Let's see what happens when we call <code>Object.prototype</code>.__ &rarr;

<pre><code data-trim contenteditable>
function f(x) { return x;}

console.log(
	Object.getPrototypeOf(f) == Function.prototype);

console.log(
	Object.getPrototypeOf([1, 2, 3]) == Array.prototype);
</code></pre>
{:.fragment}

</section>

<section markdown="block">
## Object.protoype Continued Some More

__What do you think the prototype of Array.prototype is?__&rarr;

<pre><code data-trim contenteditable>
console.log(
	Object.getPrototypeOf(Array.prototype) == Object.prototype);
</code></pre>
{:.fragment}

* __<code>Object.prototype</code>__ is at the top of the prototype chain (its the last object checked for properties)
* it provides a bunch of [methods](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/prototype#Methods) and [properties](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/prototype#Methods) to all JavaScript objects
	* __<code>toString()</code>__
	* __<code>hasOwnProperty()</code>__ (we've seen this before!)
{:.fragment}
</section>

<section markdown="block">
## Using <code>Object.create</code>

__<code>Object.create</code>__ - creates a new object with the specified prototype object and properties

<pre><code data-trim contenteditable>
// our "template" object
var protoWerewolf = { 
	description: 'hairy', 
	howl: function(thing) {
		console.log('The werewolf howls at the ' + thing + '.');
	}
};

// make a new werewolf with Object.create
var sadWerewolf = Object.create(protoWerewolf);
sadWerewolf.mood = 'sullen';
sadWerewolf.howl('moon');
</code></pre>
</section>

<section markdown="block">
## Constructors

Another way to create an object with a particular prototype is to use a __constructor__.

* a __constructor__ is basically just a function with the __<code>new</code>__ keyword in front of it
	* it's a convention to make the first letter of a constructor uppercase
	* this helps distinguish between regular functions and constructors
* an __instance__ is an object created by using __<code>new</code>__
* a constructor's __<code>this</code>__ object is bound to a __fresh, empty object__
* this is the object that's returned from invoking the constructor with <code>new</code> (unless the constructor explicitly returns a different object)
</section>

<section markdown="block">
## Constructors Continued

In the code below, both <code>sadWerewolf</code> and <code>partyWerewolf</code> are __instances__ of <code>Werewolf</code>. Note that:

* a property is added to the constructor's <code>this</code> object
* <code>this</code> is the object that's returned after calling <code>new Werewolf</code>

<pre><code data-trim contenteditable>
function Werewolf(mood) {
	this.mood = mood;
}

var sadWerewolf = new Werewolf('sad'); 
var partyWerewolf = new Werewolf('partying'); 
console.log(partyWerewolf.mood);
</code></pre>

<br>
__Let's try adding some more properties to <code>this</code>.__&rarr;

</section>
<section markdown="block">
## Constructors, Prototype 

__All constructors have a property named <code>prototype</code>.__

* the default value of a constructor's prototype is a plain, empty object that derives <code>from Object.prototype</code>
* every instance created with the constructor will have that object as its _actual_ prototype
* note that there's a difference between the constructor's prototype property that's used to set an instance's prototype versus the constructor's _actual_ prototype... __can you guess what that is?__ &rarr;<span class="fragment"><code>Function.prototype</code></span> 
* for example, we could use a constructor's prototype to add a howl method on every instance of Werewolf 

<pre><code data-trim contenteditable>
Werewolf.prototype.howl = function(thing) {
	console.log('The werewolf howls at the ' + thing + '.');
}
sadWerewolf.howl('moon');
partyWerewolf.howl('bowl of chips');
</code></pre>
</section>

<section markdown="block">
## Something Happened!

### When we added a property to the constructor's prototype, something happened! 

__How were the instances of that constructor affected?__ &rarr;

The instances immediately had access to the new property, even though they were instantiated before the prototype was set.
{:.fragment}
</section>

<section markdown="block">
## Searching for a Property

__When a property is requested from an object, where are the places that the property is searched for?__

* the object itself
* the object's prototype
* the object's prototype's prototype
* and so on up the prototype chain up until <code>Object.prototype</code>
{:.fragment}
</section>

<section markdown="block">
## Overriding Properties 

If you add a property directly to an object, it is added to the object _itself_, not the object's prototype. __What's the output of the following code?__ &rarr;

<pre><code data-trim contenteditable>
Werewolf.prototype.clothing = 'tattered shirt';
console.log(partyWerewolf.clothing);

partyWerewolf.clothing = 'backwards cap';

console.log(partyWerewolf.clothing);
console.log(sadWerewolf.clothing);
</code></pre>

<pre><code data-trim contenteditable>
tattered shirt
backwards cap
tattered shirt
</code></pre>
{:.fragment}

</section>
<section markdown="block">
## Overriding Properties Continued

__Again, when you add a property to an object, that property is added to the object itself...__

* (not the prototype)
* this happens regardless of whether or not there's already a property with the same name in the prototype 
* if there is a property with the same name in the prototype, it is _masked_ or __overridden__ by the new property
* __note that the prototype itself is not changed__
</section>

<section markdown="block">
## Where Did Those Properties Come From?

__Let's break down all of the properties of our <code>partyWerewolf</code> object and determine where they came from__ &rarr;

<pre><code data-trim contenteditable>
partyWerewolf properties
=====
</code></pre>
{:.fragment}

<pre><code data-trim contenteditable>
from partyWerewolf object
-----
clothing: backwards cap  
mood: partying 
</code></pre>
{:.fragment}

<pre><code data-trim contenteditable>
from Werewolf.prototype
-----
clothing: tattered shirt (masked)
howl: (function)
</code></pre>
{:.fragment}

<pre><code data-trim contenteditable>
from Object
-----
toString: (function)
etc.
</code></pre>
{:.fragment}

</section>

<section markdown="block">
## Overriding Properties (Last One Really?)

__Why would overriding properties be useful?__ &rarr;

* it allows for convenient way of dealing with objects that have exceptional properties (without having to create an entirely new constructor)
* while still allowing a default property to be set for all instances
* __let's override the inherited <code>toString()</code> method__ &rarr;
	* the string representation of the werewolf object should be <code>[mood] werewolf</code>
{:.fragment}

<pre><code data-trim contenteditable>
console.log(partyWerewolf);
Werewolf.prototype.toString = function() {
	return this.mood + ' werewolf';
};
console.log(partyWerewolf + '');
</code></pre>
{:.fragment}
</section>

<section markdown="block">
## Prototype: An Example

__What's the output of this code?__ &rarr;

<pre><code data-trim contenteditable>
function Monster() {
	this.scary = true;
}

function Werewolf(mood) {
	this.mood = mood;	
}

Werewolf.prototype = new Monster();
</code></pre>

<pre><code data-trim contenteditable>
Werewolf.prototype.howl = function(thing) {
	console.log('The werewolf howls at the ' + thing + '.');
}

var sadWerewolf = new Werewolf('sad');
var partyWerewolf = new Werewolf('partying');
partyWerewolf.scary = false;
</code></pre>

<pre><code data-trim contenteditable>
console.log(sadWerewolf.scary);
console.log(partyWerewolf.scary);
</code></pre>
</section>

<section markdown="block">
## Example Continued

__The output would be...__

<pre><code data-trim contenteditable>
true
false
</code></pre>

Some notes on the example:

* to inherit properties from Monster, we set our Werewolf constructor's prototype to a new Monster
* <code>var sadWerewolf = new Werewolf('sad'); </code>
* ...which is why scary was found in the prototype chain for <code>sadWerewolf</code>
</section>

<section markdown="block">
## Create Your Own!

__Create the following constructors and objects.__ &rarr;

* a Vehicle constructor that sets its wheels property to <code>4</code>
* a Car constructor that sets its convertible property to <code>false</code>
* a Bike constructor
* Bike and Car should inherit their properties from Vehicle
* modify the Bike prototype so that its wheels are always 2
* modify the Bike prototype to add a honk method (it should log 'ring ring')
* create two objects, a Bike and a Car
* have the bike honk
* print out the number of wheels for each

</section>

<section markdown="block">
## A Potential Implementation

<pre><code data-trim contenteditable>
function Vehicle() {
	this.wheels = 4;
}
function Car() {
	this.convertible = false;
}
function Bike() {
}
</code></pre>

<pre><code data-trim contenteditable>
Car.prototype = new Vehicle();
Bike.prototype = new Vehicle();
Bike.prototype.wheels = 2;
Bike.prototype.honk = function() {
	console.log('ring ring');
};
</code></pre>

<pre><code data-trim contenteditable>
var myCar = new Car();
var myBike = new Bike();
myBike.honk();
console.log(myCar.wheels);
console.log(myBike.wheels);
</code></pre>

</section>	
<section markdown="block">
## Enumerating Properties Revisited

__How do we list every property in an object?__ &rarr;

<pre><code data-trim contenteditable>
for (var prop in obj) {
	console.log(prop)
}
</code></pre>
{:.fragment}

__Let's list every property and value in <code>partyWerewolf</code> and <code>sadWerewolf</code>.__ &rarr;
{:.fragment}

<pre><code data-trim contenteditable>
for (var p in partyWerewolf) {
	console.log(p + ': ' + partyWerewolf[p]);
}
for (var p in sadWerewolf) {
	console.log(p + ': ' + sadWerewolf[p]);
}
</code></pre>
{:.fragment}
</section>

<section markdown="block">
## Own Property

__What if we only want the properties that were explicitly set on our object, rather than including inherited ones.__ &rarr;

We could use the <code>hasOwnProperty</code> method that every object inherits from <code>Object.prototype</code>!
{:.fragment}

<pre><code data-trim contenteditable>
console.log('party\n-----');
for (var p in partyWerewolf) {
	if (partyWerewolf.hasOwnProperty(p)) {
		console.log(p + ': ' + partyWerewolf[p]);
	}
}
console.log('\n');

console.log('sad\n-----');
for (var p in sadWerewolf) {
	if (sadWerewolf.hasOwnProperty(p)) {
		console.log(p + ': ' + sadWerewolf[p]);
	}
}
</code></pre>
{:.fragment}
</section>

<section markdown="block">
## What Instance do I Have?

If you have an object, and you'd like to know what constructor it came from, you can use the __<code>instanceof</code>__ operator.

* instance on left
* constructor on right

__What do you think the following code will print out?__ &rarr;

<pre><code data-trim contenteditable>
console.log(myCar instanceof Car);
console.log(myCar instanceof Bike);
</code></pre>

<pre><code data-trim contenteditable>
true
false
</code></pre>
{:.fragment}
</section>

<section markdown="block">
## About prototype and this

There are two ways to set properties automatically when using a constructor. __What are they?__ &rarr;

<pre><code data-trim contenteditable>
function Thing() {
	this.prop1 = 'some value';
}

Thing.prototype.prop2 = 'another value';
</code></pre>
{:.fragment}

* generally, you would use the prototype method if you only want one version of that object to exist
* see the [SO article]( http://stackoverflow.com/questions/422476/setting-methods-through-prototype-object-or-in-constructor-difference).
{:.fragment}
</section>

<section markdown="block">
## About Creating Objects

__There are a few ways to create objects... what are they?__ &rarr;

* object literal - <code>{}</code>
* Object.create
* new
{:.fragment}

<br>
<code>Object.create</code> seems to be gaining some traction.
{:.fragment}


</section>
<section markdown="block">
## A Few Things to Remember

__What object is at the top of the prototype chain?__ &arr;

<code>Object.prototype</code> is at the top of the prototype chain
{:.fragment}

__What is <code>Object.prototype</code>'s prototype?__ &rarr;

Its prototype is null.
{:.fragment}

__What are some properties that are inherited from <code>Object.prototype</code>?__ &rarr;

toString, hasPropertyOf
{:.fragment}

</section>
<section markdown="block">
## And Some More Questions

__What does the <code>hasOwnProperty</code> method do?__ &rarr;

return <code>true</code> if property was set on actual object rather than inherited
{:.fragment}

__What does the <code>instanceof</code> operator do?__ &rarr;

It determines whether the operand on the left is an instance of the operand on the right.
{:.fragment}
</section>
