[### Angular Questions and Answers

# **1. What is SPA? How it is different from server-side rendering and what are the pros and cons of SPA?**
    SPA - It means that we don't have anything on the backend but just client JavaScript.This client JavaScript is being loaded inside the client browser and is executed and then everything is rendered on screen just with the help of JavaScript.
    Single page applications are web based applications that only need to be loaded once, with new functionality consisting of only minor changes to the user interface. It does not load new HTML pages to display the content of the new page, but rather generates it dynamically. This is made feasible by JavaScript's ability to alter DOM components on the current page. A Single Page Application method is speedier, resulting in a more consistent user experience.


  # Sharing Data between components

     4 Methods to Share Data between Components in Angular
     Method 1: Parent to Child via @Input decorator.
     Method 2: Child to Parent via @Output decorator and EventEmitter.
     Method 3: Child to Parent via @ViewChild decorator.
     Method 4: Unrelated Components via a Service.

      https://www.samarpaninfotech.com/blog/methods-to-share-data-between-angular-components/

     Method 1: Parent to Child via @Input decorator.
                Let’s assume, you have one component, where you have some data and you want to supply that data to the child component, How it possible ??? Answer is @input. So what is @Input?? @Input is a decorator which allows you to accept the input from the parent component. Input can be imported from @angular/core.

    Method 2: Child to Parent via @Output decorator and EventEmitter
                If you want to pass data from the child component to the parent component use @Output() and EventEmitter.

                First, let us discuss what is @Output and EventEmitter, @Output is a component decorator which becomes the output for the parent component and EventEmitter is something that has the capability to propagate the event from the child component to the parent component.

                To pass data from the child to the parent, you have to emit it from the child. The parent will be listening for the event will grab the data.

    Method 3: Child to Parent via @ViewChild decorator
                Here as we know we have @output and event emitter to share the data from child to parent component, so why @Viewchild is needed ? hold on it is needed because it gives extra control to parent component to access the child events.

                Here we are just understanding by passing the data from child to parent by using @Viewchild decorator, Let’s see.



     
  # What is the difference between @ViewChild() and @ViewChildren()
          [ https://www.pluralsight.com/guides/querying-the-dom-with-@viewchild-and-@viewchildren]    
         (https://www.freecodecamp.org/news/angular-8-dom-queries-viewchild-and-viewchildren-example/)


  # What ways of binding in Angular?
              One-way Binding
              Two-Way Binding

 # What is service in Angular?
                
    1. Services in Angular are simply typescript classes with the @injectible decorator. This decorator tells angular that the           class is a service and can be injected into components that need that service. They can also inject other services as             dependencies. 
    2. As mentioned earlier, these services are used to share a single piece of code across multiple components. These services are used to hold business logic. Services are used to interact with the backend. For example, if you wish to make AJAX calls, you can have the methods to those calls in the service and use it as a dependency in files.
    In angular, the components are singletons, meaning that only one instance of a service that gets created, and the same            instance is used by every building block in the application. 
    A service can be registered as a part of the module, or as a part of the component. To register it as a part of the               component, you’ll have to specify it in the providers’ array of the module.

# What is AOT (Ahead-Of-Time) Compilation?
           The Angular Ahead-of-Time compiler pre-compiles application components and their templates during the build process.              Apps compiled with AOT launch faster for several reasons.
          Templates are embedded as code within their components so there is no client-side request for template files.
            At the end of the restore view phase of the JSF request lifecycle, Seam attempts to restore any previous long-running         conversation context. If none exists, Seam creates a new temporary conversation context.
        Application components execute immediately, without client-side compilation
        The compiler discards unused Angular directives that a tree-shaking tool can then exclude

  
# What is ViewEncapsulation and how many ways are there do to do it in Angular?
      To put simply, ViewEncapsulation determines whether the styles defined in a particular component will affect the entire application or not. Angular supports 3 types of ViewEncapsulation:
      Emulated : Styles used in other HTML spread to the component
      Native : Styles used in other HTML doesn’t spread to the component
      None : Styles defined in a component are visible to all components of the application


# What is AOT Compilation?
    Angular AOT contains mainly of components and their HTML templates.The components and templates are provided by the angular requires a compilation process before it can run in browser.AOT helps in converting Angular HTML and TypeScript code in to efficient JavaScript code while building phase before the browser downloads and runs the code.
    Here are some reasons you might want to use AOT:
    Faster rendering
    Fewer asynchronous requests
    Smaller Angular framework download size
    Detect template errors earlier
    Better security
    
# What is Dependency Injection?

    1. Using Dependency Injection we move the creation of binding dependent object otside of the class that depend on them. 2. DI       keeps the code more flexible testable and mutable. 3. Class can inherit external logic without having to create on its own. 4.      DI benefits directives, pipes and components.

    Consider all the components of an application performing common tasks like accessing database, rendering images on the view     
    etc. To avoid rewriting of code, angular services can be used. These services can then be injected into the components that         require that service.
    
# Difference between integration test and unit test?

    1. Integration test includes (“integrates”) the dependencies. Unit test replaces the dependencies with fakes in order to     
     isolate the code under test.

    2. Unit test is written for individual units or components of an application. Integration tests is written for two or more 
     units. An integration test does not test a complete workflow, nor does it test an isolated unit.

# What are ViewChild and ViewChildren in Angular?

    ViewChild is a decorator that creates a view or DOM query. 
    ViewChildren is another property decorator which is used to query the DOM for multiple elements and return a QueryList.

# What is Pipe ? Pure vs impure pipe ?

    Pipes help you to transform data from one format to another format. There have few inbuilt pipes in angular : DatePipe,     
    CurrencyPipe, UpperCasePipe, LowerCasePipe, JsonPipe.

    An impure pipe is called for every change detection cycle no matter whether the value or parameter(s) changes. 
    A pure pipe is only called when Angular detects a change in the value or the parameters passed to a pipe.

# How many directives are there?

    1. Attribute 2. Structural 3. Component
    
# component vs directive ?

    Components are a type of Directive. 
    @Directive is a decorator which is used to instruct the DOM to either add a new element 
    or, remove or modify an existing element. 
    @Component is a subclass of @Directive with one additional functionality. Using     
    @component, you can create own HTML template.
    Some of the major differences are mentioned in a tabular form

    | Component  | Directive |
    | ------------- | ------------- |
    | To register a component we use @Component meta-data annotation  | To register a directive we use @Directive meta-data     
     annotation  |
    | Components are typically used to create UI widgets  | Directives are used to add behavior to an existing DOM element  |
    | Component is used to break down the application into smaller components  | Directive is used to design re-usable components      |
    | Only one component can be present per DOM element  | Many directives can be used per DOM element  |
    | @View decorator or templateurl/template are mandatory | Directive doesn't use View |
 

# What do you mean by data binding & two way data binding.

    Types of Data Binding : 1. Interpolation & Property binding 2. Event binding 3. Two way binding

    Interpolation is used to just display/bind a piece of data in HTML UI element, such as displaying a title or a name.

    Property binding lets us bind a property of a DOM object, for example the hidden property, to some data value. It uses syntax 
    [].

    Event binding is used to handle the events raised by the user actions like button click, mouse movement, keystrokes, etc. It 
    flows from the view to the model when an event is triggered.

    In Two way binding, data flows from model to view and view to model.

# what is angular ivy
    Rendering engine: A rendering engine is a software or program inside a browser that parses and transforms HTML and CSS code so     that the browser can display it.Browser engine transforms CSS and JS and renders the result to the screen
    Browser engine transforms CSS and JS and renders the result to the screen

    However, browsers cannot render HTML and CSS codes coming from Angular or any other framework because the HTML and CSS are not     pure (they may be inside custom templates or components). Therefore, something needs to transform these components into what       the browser can render. This is where the Angular rendering engine comes in.
    Ivy rendering engine

    Ivy is the rendering engine that transforms Angular code (template HTML + TS) into pure HTML and JavaScript that the browser       understands. When this transformation is done, the browser can understand and render the resulting HTML and JavaScript to 
    display content, as illustrated in the image above.

    Ivy is a complete rewrite of the View Engine—the default engine for building Angular apps from Angular 4 until it was retired      in Angular 8. It is the third engine since the creation of Angular in 2016, and Angular has shipped with Ivy since the 
    introduction of Angular 9 till the present day.
    
    Benefits of using Ivy
    Ivy comes with many improvements, which include the following:

    AOT compilation: Ahead of Time (AOT) compiles an app before it goes to a runtime environment like a browser. AOT reduces the       load on the browser since it precompiles the app before it reaches the browser.

    Smaller bundle size: Bundle size is the amount of code a browser will have to download to load your app. Ivy downsizes the 
    bundle size through AOT and tree-shaking.

    Improved speed: Angular apps load more quickly than before, thanks to a smaller bundle size and the tree-shaking capability of 
    Ivy.

    Ivy is much faster than its predecessor because it now ships with ahead-of-time (AOT) compilation by default. AOT enables the 
    browser to load the application quickly without downloading the compiler and building the app itself.

    Just-in-time (JIT) compilation was the default compiling mechanism in previous versions of Angular, through which the browser 
    would download the compiler and build the app. However, this process was inefficient because it was slow and burdened the 
    browser.

    Note: Angular has just one compiler. AOT and JIT just refer to how and when you use the compiler. With AOT, the compiler runs 
    at build time. With JIT, the compiler runs at runtime.

    The Ivy engine is a critical part of Angular. Hence, having a basic idea of what it does is important.

# What is Angular Interceptor

    HTTP Interceptors are a concept in web development and server-side programming, typically associated with web frameworks and       libraries.

    · These interceptors allow developers to intercept and handle HTTP requests and responses globally within an application.
    HTTP Interceptors in Angular are classes that implement the HttpInterceptor interface.
    HTTP Interceptor

    · They can be used to perform various tasks related to HTTP requests and responses, such as adding headers, handling errors,         modifying the request or response data, logging, authentication, etc.

    · HttpInterceptor defines a single method called intercept, which takes two parameters: the HttpRequest and the HttpHandler.

    There are multiple real-time senarios where angular interceptors can be really useful:

        Modify HTTP headers
        Modifying the request body
        Set authentication/authorization token
        Modify the HTTP response
        Error handling
        Change the Requested URL

    Also, we can have multiple interceptors in our application having different functionality.

    



