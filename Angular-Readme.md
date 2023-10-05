### Angular Questions and Answers

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
           https://www.pluralsight.com/guides/querying-the-dom-with-@viewchild-and-@viewchildren


  

  
