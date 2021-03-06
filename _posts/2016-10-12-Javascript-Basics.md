---
layout: post
title: Javascript Basics...
---

Javascript is one of the key programming lanaguages used on the web today. Lets delve into the Basics.

**Variables**

How to define variables in Javascript?
Variable definitions should always start with the keyword 'var' (see example below).
Notice that no types are declared in JavaScript.

    var greeting = "hello";

Reason that is, is because JavaScript is a 'dynamically typed language'. 
That means JavaScript engine figures out the type of a particular variable at runtime.
And it also means that the same variable can hold different types during the life of the execution of the program.
   
**Functions**

Functions are defined by using the keyword 'function' followed by the function name.
In example below "greeting" is the Function name
    
    function greeting(){
    ...
    }
    
Another way to define a function in Javascript is by creating a variable and set it equal to a function.
If defined this way, no name is defined after the function keyword.Ex.
    
    var greeting = function() {...}
    
Functions are executed by referring to its name. Ex: greeting();
Arguments can be passed to the Javascript functions, they are defined without the keyword 'var'. 
And if you want the function to return some value , you use the 'return' keyword followed by whatever value you want to return. Ex:
    
    function greeting (name){
     return "Hello " + name;
    }
    
**Scope**

Everything in JavaScript is executed in an execution context.
For example a function invocation creates a new execution context, within which that function is executed. This execution context also gets a reference to its outer environment. 
This outer environment or context is called global scope. 
Variables and functions defined here are available everywhere.
Whereas in the function context, variables and functions defined there are only available within that function.

**Javascript Types**

Javascript has 7 built-in types : 6 primitive and 1 object type.

Object Type: This is a collection of name/value pair. Ex:
    Dog Object
    {
      name: "Goofy",
      breed: "Lab"
    }
    
Primitive Types: They represent a single immutable value. The primitive types are:

    1. Boolean  : Can only have 2 values: true or false
    2. Number   : Numeric type, represented as a double-precision 64-bit floating point.
    3. String   : Any sequence of characters used to represent text. i.e. 'text'.
    4. Null     : Null signifies lacl of value. Can only have one value: null.
    5. Undefined: Signifies that no value has ever been set. Can only have one value: undefined.
    6. Symbol   : A symbol is a unique and immutable data type. May be used as an identifier for Object Properties.


These are the basics, to start adding behaviour to you web apps. Happy coding!
    
    
    
