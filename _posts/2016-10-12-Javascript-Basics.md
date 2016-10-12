---
layout: post
title: Javascript Basics...
---

Javascript is one of the key programming lanaguages used on the web today. Lets delve into the Basics.

### Variables
    How to define variables in Javascript?
    Variable definitions should always start with the keyword 'var' (see example below).
    Notice that no types are declared in JavaScript.
     Ex: var greeting = "hello";
    Reason that is, is because JavaScript is a 'dynamically typed language'. That means JavaScript engine figures out the type of a particular variable at runtime. And it also means that the same variable can hold different types during the life of the execution of the program.
    
### Functions
    Functions are defined by using the keyword function followed by the function name. See below
    In example below "greeting" is the Function name
    
    function greeting(){
    ...
    }
    
    Another way to define a function is in Javascript is by creating a variable and set it equal to a function.
    If defined this way, no name is defined after the function keyword.Ex.
    
    var greeting = function() {...}
    
    Functions are executed by referring to its name. Ex: greeting();
    Arguments can be passed to the Javascript fucntions, they are defined without the keyword 'var'. 
    And if you want the function to return some value , you use the 'return' keyword followed by whatever value you want to return. Ex:
    
    function greeting (name){
     return "Hello" + name;
    }
    
### Scope

    Everything in JavaScript is executed in an execution context. For example a function invocation creates a new execution context whithin which that function is executed. This execution context also get a reference to its outer environment. This outer environment or context is called global scope. Variables and functions defined here are available everywhere.
    Whereas in the function context variables and fucntions defined here are only available within this function.
    
    
    
    
    
