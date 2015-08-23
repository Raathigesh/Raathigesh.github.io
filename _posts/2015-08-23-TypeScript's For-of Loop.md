---
layout: post
title: Loops: TypeScript For-of Loop
excerpt: "TypeScript provides some nice syntactical sugar to write readable code and get around some of the JavaScript language quirks."
modified: 2015-08-23
tags: [TypeScript, JavaScript]
comments: true
---

TypeScript provides some nice syntactical sugar to write readable code and get around some of the JavaScript language quirks. 

If we want to iterate through an array of items, we could use for loop as below and get things done.

{% highlight javascript %}
var Items = ["Key", "Phone", "Car"];

for (var x = 0; x < Items.length; x++) {
	console.log(Items[x]);
}
{% endhighlight %}

I think you would agree this code is not so readable.

## For-In Loop
JavaScript also has a For-In loop which we could use to iterate over an array as below but IT DOESN'T WORK AS EXPECTED.

{% highlight javascript %}
var Items = ["Key", "Phone", "Car"];

for (var x in Items) {
	console.log(x);
}
{% endhighlight %}

Instead of printing out the items in the array to the console, the above code prints out the index of the array as follows.

{% highlight javascript %}
> 0
> 1
> 2
{% endhighlight %}

Well that sucks.

## TypeScript Is To Rescue
No need to worry at all. TypeScript is awesome at doing type checking but it also got some nice helpers which could help us to write more readable code. 

### The For-Of Loop Of TypeScript
Since the For-In loop of JavaScript is a disappointment, the TypeScript team decided to introduce a new loop called For-Of loop which looks like this.

{% highlight javascript %}
var Items = ["Key", "Phone", "Car"];

for (var x of Items) {
	console.log(x);
}
{% endhighlight %}

This code prints out the elements in the array as we would expect.

{% highlight javascript %}
> Key
> Phone
> Car
{% endhighlight %}

But under the hood TypeScript is translating this into good old for loop as below.

{% highlight javascript %}
var Items = ["Key", "Phone", "Car"];
for (var _i = 0; _i < Items.length; _i++) {
    var x = Items[_i];
    console.log(x);
}
{% endhighlight %}

Take a look at the [live demo here.](http://www.typescriptlang.org/Playground#src=var%20Items%20%3D%20%5B%22Key%22%2C%20%22Phone%22%2C%20%22Car%22%5D%3B%0D%0A%0D%0Afor%20(var%20x%20of%20Items)%20%7B%0D%0A%09console.log(x)%3B%0D%0A%7D)

The advantage of this is, our code looks sexy and readable and I personally think that is awesome.


