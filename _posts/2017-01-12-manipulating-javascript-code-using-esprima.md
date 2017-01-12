---
published: false
---
## Manipulating JavaScript Code Using Esprima

I'm a big fan of tools. Code editors saves a ton of effort by allowing us, developers, to be productive. For  example if we have to rename a variable, simple, just ask the editor to do so, and the editor will rename all the occurrence of that particular variable. But what's going under the hood to achieve this?

Let's say we have a JavaScript code snippet and we want to rename all the variables to something else using JavaScript.

We could just do a simple string replacement but as you can imagine things would get tricky real soon when you have complex. We can not trust string replacement to be accurate. We could one step further and write some complex regular expresion to get this done. But again, regular expressions are just hard, tricky and simple not fun. If you are a regular expression wizard, you would be fine. Else, it's going to be a trial and error experiment.

### Meet the beast, Abstract syntax tree




