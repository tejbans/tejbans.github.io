---
layout: post
title: Object Architecture Simplified...
---

### Object Architecture

As the name implies,  its all about the Objects. But what does that really mean?
Let’s look at some real-world examples to see.

Imagine an object that most people can relate to, a car. How can we describe a car?

![alt text](http://tejbans.github.io/images/Pagani.jpg)


 Well, it has attributes such as the color, make, model, year, mileage, and vin. Each of these attributes make each car what it is. In Object Oriented Programming, the features that describe an object, are called properties.

### Behavior of an Object

The next question is, what are the actions a car can do, or can be done to the car? Let’s take some of the obvious ones:

Car can drive
Car can carry passengers
Car can Stop

In Object Oriented programming, these actions, are called **methods**. They allow the objects to do things, and, also provide a way to read/write the properties of the object.

For example - After you buy the car, you may decide you don’t like the color and want it repainted to white. In object oriented programming, we call these setter methods, which are just special methods for setting properties on an object. On the other hand let’s say we get stopped for a speeding ticket, and the officer wants to get the VIN number. You would read the VIN through a getter method.


### Creating Cars/Objects

Now that we have properties, methods, and ways to read or set/change the properties through setter and getter methods, you may be wondering, how do we create the car/objects in the first place?

The answer is, using a factory or as it is referred to in object orientation a constructor . A constructor is a special method which creates an object. After you’ve created an object, you have an instance of it. This process is called **instantiation**.


Example


Lets go back to the car example. We are at the factory, and we instantiate our car by using a constructor method to create it. This special method takes inputs for the model, color, and VIN number, and outputs a brand new car.

At this point , we’ll change terms, and instead of calling these objects, we’ll now call them classes. Example the Car Class

![alt text](https://github.com/tejbans/tejbans.github.io/blob/master/images/classes_and_objects.jpg "Car Objects")

Classes are “blueprints” for creating a group of objects.
– A car class to create car objects

• The blueprint defines
– The class’s properties as variables
– The class’s behavior as methods


### How can we create Trucks/ Buses ?

Now how do we create a Truck or Bus. How can the above knowledge help us be more efficient at creating any type of Vehicle not just a car.


Using our example we  now have a class called vehicle, with all the properties and methods common to our three types of vehicles. This is called the parent class, and the three vehicles are it’s subclasses. 


What’s important to note is that those common properties and methods only need to be defined in the parent class level. The children automatically have access to these, and so defining them there is not necessary. This concept is called inheritance.


### Inheritance

In the subclasses, we only need to define the things that are unique to them. For example, for a truck the maximum amount of cargo is important, so this could be a property, and a bus may have a method to loadPassengers or unloadPassengers.

Also imagine that we started to produce other types of vehicles, the inheritance concept really makes things easier to add them, as we simply need to define the properties which are not already covered by the common vehicle class.

In OOP, you will sometimes have classes that are not intended to be used directly (such as our vehicle class in this example), but instead simply exist as a common parent. In these cases, it is meant for the subclasses to be used. In other cases, the parent and subclasses can be used. Or, subclassing can be a way for you to extend an existing class that you would like to add functionality to.


### Summary


To summarize, here are some of the main object oriented programming concepts:


