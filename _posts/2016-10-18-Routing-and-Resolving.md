---
layout: post
title: Routing and Resolving
---


Single page web applications (SPAs) are very popular nowadays. But what is an SPA?

From wikipedia.

>A single-page application (SPA) is a web application or website that fits on a single web page with the goal of providing a user experience similar to that of a desktop application. In an SPA, either all necessary code – HTML, JavaScript, and CSS – is retrieved with a single page load, or the appropriate resources are dynamically loaded and added to the page as necessary, usually in response to user actions.

But wouldn't even a simple app, have at least a couple of different views, where the majority of the content on the page will have to be replaced with some other content?

How do we split our app views into logical chunks? Preferably with different url's. Also users should be able to get from one view in the application to another view.


And this is where **routing** comes in. Routing is how we define the different views in a angularjs application.


### Routing

The two most commonly used packages for defining the routes in an angularjs app are **ngRoute** and **ui-router**. In ngRoute every route must be represented by a url. 

In ui-router (which is a open source project), the main concept is of a ‘UI state’. For example, you can have a route with no unique url for that route whatsoever.However, url routing is also supported so you can have a state that is associated with a particular URL.

Let's look at ui-router in more details.

After you have installed and referenced ui-router in the your project.
The first step is to inject the ui-router as a dependency  in your module.

	angular
     	.module(‘app’, [ui.router])

Second, designate where in your HTML page you would like the views to be dynamically placed. This is achieved by placing a custom directive called **ui-view**.
	
	<ui-view></uiview>

### Defining the routes

ui-router comes with two essential services, $state and $urlRouter. We have to inject the provider versions of these services into the angular.config method to configure the routes.

	angular
	  .module('app', ['ui.router'])
	  .config(function($stateProvider, $urlRouterProvider){
	    $stateProvider
	      .state('home',{
		url: '/',
		templateUrl: 'app/templates/home.html',
		controller: 'HomeController as ctrl'
	      })
	$urlRouterProvider.otherwise('/');
	  });


So we give each state a unique name that we'll be able to refer to throughout our application, **home** in above example.

We can also optionally associate a URL with a particular UI state. In this case its **/**.

Then we specify an HTML template, the contents of which will be inserted into the ui-view tag in our HTML page. In example above its **home.html**.

Finally, we specify the controller that is associated with the view template (Ex. HomeController).

For cases where the URL has been mistyped by the user or its just a non-existent url, a common practice is to configure the URL router service provider by executing it's **otherwise** method. This configuration tells the ui-router that when it tries to match a browser URL with a URL associated with a particular declared state and it can't find any matches, it should default to the URL declared in the otherwise method. So in example above it will default to the ‘/’ state.



### Resolving

In many cases when we navigate to a state/url, we might require some data from the server.

We could do that in the controller, but that means that the view will usually load first and then  the data. This does not lead to a very good user experience. So what's the solution?

The solution is to use the **resolve** property in our route configuration. Let's look at an example. 

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

Here in our state called *expenses* we have defined a **resolve** property. On the property we define a key called ‘expenses’  which is assigned a function and injected with a service like ExpenseService in above example. And we are calling a asynchronous method getExpenses() on the service, which returns a promise.

Once the promise is resolved ui-router will render the view.

Now how do we use this access this data? To access the data we inject the key defined in the resolve property - ‘expenses’ in this case, into our controller.

	function ExpensesController(expenses) {
		var ctrl = this;
		ctrl.expenses = expenses;
	}

This way the data will be fetched first and then the view is rendered.
