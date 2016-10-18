---
layout: post
title: Object Oriented Programming
---


Single Page web applications(SPAs) are very popular nowadays. But what is an SPA?

>From wikipedia.

>A single-page application (SPA) is a web application or website that fits on a single web page with the goal of providing a user experience similar to that of a desktop application. In an SPA, either all necessary code – HTML, JavaScript, and CSS – is retrieved with a single page load,[1] or the appropriate resources are dynamically loaded and added to the page as necessary, usually in response to user actions.


I first heard of SPAs when I started to learn the javascript framework AngularJS. And routing is one of the key concepts because, even a simple app, will, probably have at least a couple of different views, where the majority of the content on the page will have to be replaced with some other content.  Users will need to be able to get from one view in your application to another view.

So routing is how we define the defiirent views in a angularjs application


### Routing

The two most commonly used packages for defining routing/navigation in an angularjs app are ngRoute and ui-router. In ngRoute  every route must be represented by a URL. 

In ui-router( which is a open source project), the main concept is of a ‘UI state’. For example you can have a route with no unique url for that route whatsoever. However, URL routing is  also supported so you can have a state that is associated with a particular URL. Also nested views are supported. Let look at ui-router in more details. After you have installed and referenced ui-router in the your project.

The first step is to inject the ui-router as a dependency  in your module.

angular
     .module(‘app’, [ui.router])

Second, designate where in your HTML page you would like the views to be dynamically placed. This is achieved by placing a custom directive called ui-view.
	<ui-view></uiview>

Now to  define the routes. ui- router comes with two essential services, $state and $urlRouter. We will inject the provider versions of these services into the angular.config method to confugure the routes. Like below

angular
  .module('app', ['ui.router']])
  .config(function($stateProvider, $urlRouterProvider){
    $stateProvider
      .state('home',{
        url: '/',
        templateUrl: 'app/templates/home.html',
        controller: 'HomeController as ctrl'
      })
$urlRouterProvider.otherwise('/');
  });


As you see we give each state a unique name that we'll be able to refer to throughout our application. Ex. ‘home’ in above We can also optionally associate a URL with a particular UI state. Then  we specify an HTML template, the contents of which will be inserted into the UI view tag in our HTML page. (home.html in example above). Finally we specify the controller that is associated with the view template( Ex. HomeController).

For cases where the URL has been mistyped by the user or just a non-existent url, a common practice is to configure the URL router service provider by executing it's otherwise method. This configuration tells the UI router that when it tries to match a browser URL with a URL associated with a particular declared state and it can't find any matches, it should default to the URL declared in the otherwise method. So in example above it will default to the ‘/’ state.



Resolving

In many cases when we route to a state or url, we might require some data from the server. We could do that in the controller, but that means that the view will usually load first and then  the data.  This does not lead to a very good user experience. So what's the solution?

Solution is to use the ‘resolve’ property in our route configuration. Let look at an example . 

 .state('expenses',{
        url: 'expenses',
        templateUrl: 'app/templates/home/expenses.html',
        controller: 'ExpensesController as ctrl',
        resolve: {
          expenses: function(ExpenseService){
            return ExpenseService.getExpenses();
          }
        }
      })

Here in our state called ‘expenses’  we have defined a resolve property.  In the property we define a key called ‘expenses’  which is assigned a function  injected with a service( ExpenseService). And we are calling a asynchronous method ‘getExpenses’ on the service.
This returns a promise . Once the promise is resolved ui-router will render the view.

Now how do we use this access this data? To access the data we inject the key ‘expenses’ in this case into our controller.

function ExpensesController(expenses) {
	var ctrl = this;
	ctrl.expenses = expenses;
}

