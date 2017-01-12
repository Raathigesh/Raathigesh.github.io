---
published: false
---
## Manipulating JavaScript Code Using Esprima

I'm a big fan of tools. Code editors saves a ton of effort by allowing us, developers, to be productive. For  example if we have to rename a variable, simple, just ask the editor to do so, and the editor will rename all the occurrence of that particular variable. But what's going under the hood to achieve this?

Let's say we have a JavaScript code snippet and we want to rename all the variables to something else using JavaScript.

We could just do a simple string replacement but as you can imagine things would get tricky real soon when you have complex. We can not trust string replacement to be accurate. We could one step further and write some complex regular expresion to get this done. But again, regular expressions are just hard, tricky and simple not fun. If you are a regular expression wizard, you would be fine. Else, it's going to be a trial and error experiment.

### Meet the beast, Abstract syntax tree
Accodring to wikipedia, Abstract syntax tree is a tree representation of the abstract syntactic structure of source code written in a programming language.

Abstract syntax tree (AST) helps to represent a piece of code in a form of a tree. This allows us to traverse the tree and examine the code or manipuate the tree nodes as we want.

### Esprima, The JavaScript Parser
Tranforming a piece of code into an AST is not a simple task. A source code parser is required to do this job for us. There are quite a few JavaScript parsers availble to choose from. But Esprima is one of the very  stable and actively maintained parser out there.

### Traversing an Abstract Syntax Tree
An AST is prety complex sturcture and if you try to traverse on your own, you could feel that it's not so easy after all. But not to worry, tools like `estraverse` makes traversing JavaScript ASTs a breeze.

### Generating code from an Abstract Syntax Tree
So we have an AST, we could traverse and change it as we want. But at the end of the day, we have to turn the AST back to code for it be usefull. Again we need someone to help with this as well. Thank fully `recast` got it corvered. Recast has a print method which takes in an AST and generates the code.



