---
published: true
layout: post
excerpt: ""
modified: 2015-09-26T00:00:00.000Z
tags: 
  - TypeScript
  - JavaScript
comments: true
---


VS Code proving to be a very capable editor to me. In this post I will go over the steps to debug [Mocha](https://mochajs.org/) unit tests for NodeJs in VS Code.

Let's assume you have all your tests under a folder called **_tests_**. 

1. Create a launch.json file and add a new task named **Run Mocha**.
2. Install Mocha globally using the command **npm install mocha -g**
3. Configure the VS Code task as below in the launch.json file.
{% highlight javascript %}
{
	"version": "0.1.0",
	// List of configurations. Add new configurations or edit existing ones.
	// ONLY "node" and "mono" are supported, change "type" to switch.
	"configurations": [		
		{
            "name": "Run mocha",
            "type": "node",
            "program": "C:/Users/John/AppData/Roaming/npm/node_modules/mocha/bin/_mocha", //Globally installed mocha
            "stopOnEntry": false,			
            "args": ["test/**/*.js"], // Specify which are the file you want the runner to pick up.
            "cwd": ".",
            "runtimeExecutable": null,
            "env": { 
				"NODE_ENV": "production"
			},
			"sourceMaps": true, // If you are using Typescript and you alread have sourcemaps generated in the test folder, simple specifying this flag will give the luxry of debugging the typescript test instead of JavaScript.
			"outDir": "test/" // This is the directory where your tests are located.
        }
	]
}
{% endhighlight %}


