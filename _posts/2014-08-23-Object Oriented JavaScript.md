---
layout: post
title: Object Oriented JavaScript
excerpt: "Object Orientation helps to write maintainable code. JavaScript is not the best language to write object-oriented code but we can write object-oriented JavaScript with some workarounds."
modified: 2014-08-23
tags: [JavaScript]
comments: true
image:
  feature: texture-feature-01.jpg
---
Object Orientation helps to write maintainable code. JavaScript is not the best language to write object-oriented code but we can write object-oriented JavaScript with some workarounds. I’m not an expert in this subject but here are some basic points to get started with Object Oriented JavaScript.

Basic building blocks of object orientation is classes. To create a class in JavaScript, we need to use the function keyword. The following code shows how to define a simple “Student” class.

{% highlight javascript %}

function Student() {

}

{% endhighlight %}

Each class will hold some properties which belongs to them. We can add properties to the already created “Student” class as below. Let’s accept the initial value of these properties through the constructor as well.

{% highlight javascript %}

function Student(firstName, lastName) {

this.firstName = firstName;

this.lastName = lastName;

}

{% endhighlight %}

Next is to create methods to perform actions on “Student” instances. Let’s say we want a method to return the full name (firstName + lastName) of the student. One way we can do this by simply adding a “getFullName” function to out “Student” Class like below.

{% highlight javascript %}

function Student(firstName, lastName) {

this.firstName = firstName;

this.lastName = lastName;

this.getFullName = function()
           {
               return this.firstName + " " + this.lastName;
           }
}

{% endhighlight %}

The above method will work as expected. It will work but is this the right way to do it ? Not Exactly.

The problem with the above approach is that every instance of the student object will get a copy of the “getFullName” method. If we create 5000 instances of the “Student” class, there will be 5000 copies of “getFullName” method in the  memory which is really unnecessary duplication. So how to handle this issue ? Do not worry. “Prototype”  is to rescue.

Instead of defining the method inside the “Student” class, let’s define it to the prototype of the “Student” class like below.

{% highlight javascript %}

Student.prototype.getFullName = function(){

         return this.firstName + " " + this.lastName;

}

{% endhighlight %}

So we created a student class. Added properties and methods to it. Not its show time. Lets create some object.

{% highlight javascript %}

var John = new Student("John", "Malcom");
var Peter = new Student("Peter", "Hein");

John.getFullName();
Pater.getFullName();

{% endhighlight %}

Happy OOP with JavaScript. After-all its JavaScript.
