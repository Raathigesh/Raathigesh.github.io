---
layout: post
title: JavaScript – Parsing XML Document and Query Using Xpath
excerpt: "JavaScript supports some heavy XML processing but things get messy when it comes to cross browser support. As usual there is an IE way of doing thing and the rest of the browsers way of doing things."
modified: 2014-08-04
tags: [JavaScript]
comments: true
image:
  feature: texture-feature-05.jpg
  credit: Texture Lovers
  creditlink: http://texturelovers.com
---

<section id="table-of-contents" class="toc">
  <header>
    <h3>Overview</h3>
  </header>
<div id="drawer" markdown="1">
*  Auto generated table of contents
{:toc}
</div>
</section><!-- /#table-of-contents -->

JavaScript supports some heavy XML processing but things get messy when it comes to cross browser support. As usual there is an IE way of doing thing and the rest of the browsers way of doing things. So there was a requirement to parse XML document and query specific nodes using Xpath. One easy way of XML parsing and querying is jQuery. But jQuery parsing can be slow sometimes depending on the size of the document we are parsing. After some googling below piece of code did the trick.

## Code Snippets

{% highlight javascript %}

 function getSingleXmlNode(data, xpath) {
        try {
            var xmlDoc = new ActiveXObject("Microsoft.XMLDOM");
            xmlDoc.async = "false";
            xmlDoc.loadXML(data);
            return xmlDoc.selectSingleNode(xpath);
        } catch (e) {
            var doc = (new DOMParser).parseFromString(data, 'text/xml');
            var it = doc.evaluate(xpath, doc, null, 5, null);
            var node = it.iterateNext();
            return { text: node.textContent };
        }
    }

{% endhighlight %}

So Happy XML parsing :)
