---
published: false
---
## Using Abstract syntax tree to manipulate code

Code editors save a ton of effort by allowing us, developers, to be productive. For example if we have to rename a variable, just ask the editor to do so, and the editor will rename all the occurrence of that particular variable. But what's going under the hood to achieve this?

Let's say we have a JavaScript code snippet and we want to rename a variables to something else, We could just do a simple string replacement but as you can imagine, things would get tricky real soon when your code gets complex. We can not trust string replacement approach to be accurate. We could go one step further and write some complex regular expression to get this done. But again, regular expressions are just hard, tricky and simply not fun. If you are a regular expression wizard, you would be fine for start. Else, it's going to be a trial and error experimenent.

### Meet the beast, Abstract syntax tree (AST)
But not to worry, Abstract syntax trees are here to save the day. Accodring to wikipedia, Abstract syntax tree is a tree representation of the abstract syntactic structure of source code written in a programming language.

Abstract syntax tree (AST) helps to represent a piece of code in a form of a tree. This allows us to traverse the tree and examine the code or manipuate the tree nodes as we want.

### Converting code to AST
Tranforming a piece of code into an AST is not a simple task. A source code parser will do this job for us. There are quite a few JavaScript parsers availble. But Esprima is one of the very stable and actively maintained parser.

But instead of using Esprima, i'm going to use another too called `recast`. Recast uses Esprima internally to construct AST. But you might ask why not use Esprima directly rather than using another library which uses Esprima internally. Well, `recast` have some additional functionality we will require later.

```javascript
import recast from 'recast';

// this is the code we have to modify
var code = 'var x = 5;';

// parse the code and get the AST
var ast = recast.parse(code);
```

### Changing the AST and Generating code
So we have an AST, we could change the tree as we want. Let's change the variable name from `x` to `y` with the following line of code.

```javascript
// modify the AST as you want.
ast.program.body[0].declarations[0].id.name = "y";
```

But how do I get to know the node that is holding the variable name. Meet [AST Explorer](https://astexplorer.net/), a tool which will generate the AST the browser when you specify the code. Examine how the AST of our code snippet looks like [here](https://astexplorer.net/#/TEMnzHmo3M).

But at the end of the day, we have to turn the AST back to code for it be usefull. Again we need someone to help with this as well. Thank fully `recast` got this corvered. Recast has a print method which takes in an AST and generates the code.

```javascript
var updatedCode = recast.print(ast).code;
```

Take a look at the complete [exmaple here](http://www.webpackbin.com/4ygV02xUM).

### Traversing an Abstract Syntax Tree
In the above example we accessed the node directly and changed it. But if you want to examine a huge tree, you often want to traverse the tree node by node. An AST is complex sturcture and if you try to traverse on your own, you would feel that it's not so easy after all. But not to worry, tools like [`estraverse`](https://github.com/estools/estraverse) makes traversing JavaScript ASTs a breeze.

### Conclusion
Manipulation code directly using string manipulation is not much fun. Once you convert the code into a Abstract syntax tree (AST) using a parser such as Esprima, traversing and manipulating it becomes straight forward. Once you manipuate the tree, you can convert back into code.

I hope this would give you a very brief idea on how to get started with code manipualtion in JavaScript.
