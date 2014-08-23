---
layout: post
title: Converting Json Object to XML string in JavaScript
excerpt: "Here is a snippet which will covert JSON objects to XML. But keep in mind attributes are not supported."
modified: 2014-08-23
tags: [JavaScript]
comments: true
image:
  feature: texture-feature-01.jpg
---
Here is a snippet which will covert JSON objects to XML. But keep in mind attributes are not supported.
## Code Snippets

{% highlight javascript %}

function objectToXml(obj) {
        var xml = '';

        for (var prop in obj) {
            if (!obj.hasOwnProperty(prop)) {
                continue;
            }

            if (obj[prop] == undefined)
                continue;

            xml += "<" + prop + ">";
            if (typeof obj[prop] == "object")
                xml += objectToXml(new Object(obj[prop]));
            else
                xml += obj[prop];

            xml += "<!--" + prop + "-->";
        }

        return xml;
    }

{% endhighlight %}

Example Usage

{% highlight javascript %}

 var myAwesomeObject = {
     Name : {
         Text : "Mr.Awesome",
         Address : "No 0, Awesome Lane, Awesome Land"
     }
};

var xmlString = objectToXml(myAwesomeObject);

{% endhighlight %}

So that’s how our awesome XML generator works.

So Happy XML parsing :)
