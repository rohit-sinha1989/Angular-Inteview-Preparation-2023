[# Angular-Inteview-Preparation-2023

## RxJS -

# Stream vs Array
The Observables are based on the idea of streams, which means that the data can come from various
points of time and the number of emitted values might be theoretically infinite.
It can be compared to a conveyor belt situation where the items are processed one at a time.
Most of us are used to working with arrays where all the data is already known and available to us.
However, in the world of Observables, which allows us to emit the values at any point of time, we
have to change our approach and think in a stream-like way.
In this case, we have a few fruits and vegetables in our array.
This might be our shopping list or a list of things that are available at the shop nearby.
What is common for all arrays is that each of the values can be easily accessed and you can see how long the array is. Now, how should we approach a stream?
How can we work with them?
First, the items in a stream can come at various points in time, so let's draw a timeline.
As time passes, some data might show up in our stream. For example, let's say we've just entereda local grocery store and we go further and see some products.
First, we see a lemon.We can react somehow to it or not.For example, we can take this lemon and put it into our shopping basket,if it was on our shopping list. Then we move further, time passes,we see a coconut. Again, we can take it or not.We take the action at the time we see this product.Later, we might find an onion. Again,we can do something with it or not. And even later, we could see a mushroom.
And of course, this kind of mushroom shouldn't be found in the store,so maybe if something like this happens, we might react to it by calling the store manager.
If we would go further, there might or might not be more products that we will see.And if we would like to name this particular stream, we could say it's a stream of the products which we see.Each time we would enter the grocery store, we would notice different products at different points
in time. As you can see, the stream approach is more about reacting to the things as they show up. We don't know the next value and whether it will appear at all.We just provide some code that will react to the emitted data in case it shows up. This approach is called reactive programming, and the Observables are based around this idea.



# What is observable, observer and subscribe in angular?

https://stackoverflow.com/questions/51520584/what-is-observable-observer-and-subscribe-in-angular

   An Observable can be thought of as various data sources(ex: (userInputs)Events, HttpRequests etc).

here creating our custom observable.

    var observable = Observable.create((observer: any)=>{
       observer.next("Hii")
       observer.next("how are you")
       observer.complete()
    observer.next("This will not send to observer")
});
next() used to emit values to observer
complete() indicates that completion of observable is notified.
An Observer is basically who subscribes to Observable.
```
observable.subscribe(
    (data: any) => console.log(data), // for handling data
    (error: any) => console.log(error), // for handling error
    () => console.log('completed'); // for handling completion);
```

   <img width="1334" alt="Screenshot 2023-10-01 at 2 11 05 AM" src="https://github.com/rohit-sinha1989/Angular-Laerning-2023/assets/42764266/c353a89e-97f0-47f4-a6e8-b24a445673de">


    #Teardown Loagic in Observable
    the Teardown logic can be used by the Observable to

It's clean up after itself to prevent memory leaks or to provide cancellation logic,for example. If we would have an Observable which would call the server using an HTTP request, we could abort that HTTP request in the Teardown logic.So if the user would unsubscribe before the request finishes, the HTTP call would be aborted.
So the Teardown logic is the place to provide the behavior for the clean up and cancellation. This is an important advantage of the Observables.They provide a way to cancel ongoing processes that were initialized by the Observable.
```
const observable3$ = new Observable((subscriber3) => {
  subscriber3.next('Alice');
  subscriber3.next('Ben');
  setTimeout(() => {
    subscriber3.next('Charlie');
    subscriber3.complete();
  }, 2000);
  //Teardown logic
  return () => {
    console.log('Teardown logic Executed');
  };
  //End
});
console.warn('subscription3 started');
const subscription3 = observable3$.subscribe({
  next: (observer3) => console.log(observer3),
  error: (err) => console.log(err),
  complete: () => console.log('Completed...!'),
});
console.warn('subscription3 Ended');](url)
```



## Hot and Cold Observable

we had Observables which generated some notifications every time we subscribed to them. For example, we've implemented a few Observables which always returned
to the same set of values.And we also saw an Observable which started a new interval and then produced the values based on the
interval triggers.In these cases, for each new Subscription, the Observable produced a new set of values.
The Observables which work this way are described as Cold Observables.And on the other hand, we can have Hot Observables, where the Observable's
logic connects to some common, shared source, for example, a DOM event like a click on a button.
So if we would have multiple Subscriptions to the same Observable, each active Subscription would receive the same values at the same time.


## Cold
First, let's start with the Observable, which we've done quite a few of - the Cold Observable. We had an Observable which when we subscribed, produced and emitted values, sometimes immediately, sometimes with a time delay. We have even created an Observable which used intervals. All those Observables produced the values independently for each Subscription. So, let's have a look at an example of a Cold Observable, which would produce and emit three values spread in time, for each new Subscription. Let's say we subscribe to such Observable at this point of time and the code inside of the Observable is run, so it starts producing the values for this Subscription. And produces the first value after some time. Then, we create another Subscription to the same Observable at this point of time, and the Observable's logic is run again, this time for our second Subscription. And if the time would go on, we would see the values as they are produced independently for each Subscription. This is exactly how the Observables we've created so far looked like. All values were produced independently for each Subscription, and this is what describes them as Cold Observables. OK, now let's have a look at another example of a Cold Observable. The Cold Observables don't always need to emit the exact same values at the same points of time, after subscribing. In this example, we'll see a Cold Observable which will produce different results for each Subscription. Let's imagine an Observable, which would call an HTTP endpoint each time we subscribe. It would still be a Cold Observable as each Subscription would produce a separate HTTP request. Now, let's say we create three Subscriptions to such Observable at the same time. This means that each Subscription will run the Observable's logic independently. So, there will be a separate request made for each one of them. The Observable's logic will wait for the HTTP response and then emit it as a next notification and complete. So, let's wait for some request to finish. And as we know, the servers sometimes respond very quickly, sometimes slowly, and there might also be some timeout or other failure. So, let's say the first to receive the response is the second Subscription. A value with the response is emitted. And the Observable also emits a complete notification, ending the Subscription as it has nothing more to do. Then, after some more time, the first call gets the response, so the Observer for the first Subscription would receive the response and the complete notification. And lastly, let's say the third response timed out or there was some server error, which means that for the third Subscription, the Observable's code will emit an error with the error details as the payload. So as you can see, a Cold Observable can also emit different values for each Subscription. The important thing to remember here is that we can say that the Observable is Cold when it produces the source of the data inside of the Observable's logic. Like in this example, the Observable produced a separate, independent HTTP call for each Subscription. Let's now move on to the coding section in which we'll also make HTTP calls to see a similar Cold Observable in action. In this part, we'll call an API using an HTTP request. We'll use the Random Data API from random- data-api.com. This is an open API which allows to easily test HTTP calls. We'll be using a URL which will return random names. So if I load this URL in the browser, we can see that it returns some JSON object with various names. For example, we can see the first name 'Conchita'. If I would refresh now, we can see a new set of values. This time the first name is 'Jamel'. OK, looks awesome. Let's copy this URL and move to our code editor. OK, we'll use the 'ajax' function from the RxJS library to call the API. The 'ajax' function can be imported from rxjs/ajax. rxjs/ajax. OK. Now, what is this 'ajax' function? So the 'ajax' function is a helper function provided by RxJS. Such helper functions are called Creation Functions or Creation Operators, and we'll talk more about them in the next section. In short, these functions create a new Observable for us, so we don't have to use the 'new Observable' constructor and provide the whole logic every time we'd like to create a new Observable. For example, this 'ajax' function will create an Observable which will send an HTTP request to the endpoint provided as an argument. So, let's provide the URL to the API we've got in our clipboard. I'll paste it in. And now we can subscribe to our new AJAX Observable. And let's provide the handler for the data we will receive. And once again, we'll just console log it. OK, let's now run the code. And we can see that we've successfully received the AJAX response from the API. And inside of the response, we can see the same object we just saw with some random names in it. So this endpoint responds with random names each time we call it. This is cool, but this example is about explaining what the Cold Observable is about. So I'd like to show you what would happen if we would subscribe to this Observable multiple times. So, each Subscription should make a separate HTTP call. Before we add other Subscriptions, let's prepare our code a bit. So, let's assign our AJAX Observable to a const. Like so. And adjust our current Subscription to use it. And let's also not console log the whole data set we receive, but just the first name. And as we're using TypeScript, we should also provide the type of the response over here. For now, I'll just put 'any' to solve the typing issues. OK, let's also add 'Sub 1:' over here, to the console log, as a reference to see which Subscription received what the value. Now, let's add two more Subscriptions. Let's just duplicate the first one and adjust the console logs. So if we would run the code now, we should have three HTTP requests made, one by each Subscription. And each Subscription should receive a random value. Let's check whether that's true. I'll save the code now to run the code. And we can see that each of our Subscriptions received a different response, which means that the Observable created with the 'ajax' function is an example of a Cold Observable as it produced a new source of emissions, namely a new HTTP request for each Subscription.


## Of
The 'of' function allows us to create an Observable, which emits a set of values and completes. So, when we subscribe to such Observable, all values that we have provided as arguments will be emitted immediately as next notifications, and then, the Observable will complete, ending the Subscription.

```
of('Rohit', 'Rahul', 'Priyanka').subscribe({
  next: (value) => console.log(value),
  complete: () => console.log('completed..!!'),
});

```
/* After trying that, we'll recreate the same behavior by using the 'new Observable' constructor. */

```
const names$ = new Observable<string>((subscriber) => {
  subscriber.next('Rohit');
  subscriber.next('Rahul');
  subscriber.next('Priyanka');
  subscriber.complete();
});

names$.subscribe({
  next: (value) => console.log(value),
  complete: () => console.log('Completed..!!'),
});

```
//End

/* And finally, we'll try to recreate the 'of' creation function.
So, we'll create a Creation Function ourselves. */
```
function ourOwnOf(...args:string[]): Observable<any> {
  return new Observable(subscriber=>{
    for(let i =0; i<args.length;i++)
    {
      subscriber.next((args[i]));
    }
    subscriber.complete()
  });
}

ourOwnOf('Rohit', 'Rahul', 'Priyanka').subscribe({
    next: (value) => console.log(value),
    complete: () => console.log('completed..!!'),
  });
```

## form
  For example, it can convert an array into an Observable.It works the same way as the 'of' creation function,however, in the case of 'from', you provide an array with the values instead of providing multiple arguments.
  ```
from(['Rishaan','Ritisha','Priyanka']).subscribe({
  next: value => console.log(value),
  complete: () => console.log('completed')
})
```

Now, let's move on to the second part of this coding section. We'll convert a Promise into an Observable. Now, why would we even want to do something like this? It is useful when we already have some code or API exposed as a Promise and we'd like to use this Promise in the Observable world to be able to use all of the tools provided by RxJS as a part of more complex asynchronous code or to combine it with other Observables.

```
const newPromise = new Promise((resolve, reject) =>{
  //resolve('Resolved...!!');
  reject('Rejected ..!!!');
})

const newObservableFromPromise$ = from(newPromise);

newObservableFromPromise$.subscribe(
  {
    next: value => console.log(value),
    error: err => console.log('Error :', err),
    complete: () => console.log('Completed ...!')
  }
)

```

Summary : the Observable created using the 'from' function with a Promise passed to it uses the 'then' and 'catch' methods
on the Promise, and then passes the resolved value or rejection error as a next or error notification.

## Let's now have a look at the 'fromEvent' creation function. The 'fromEvent' function allows us to create
It supports multiple event targets, including the DOM event targets, the Node.js event emitter and even jQuery events. This is useful to create an Observable which will emit events each time the user clicks on a button, inputs something into a form field or resizes the window, for example. Let's now consider that we create an Observable using the 'fromEvent' function, which binds to the click event on a button DOM element. And subscribing to this Observable will work similarly to using the 'add Event Listener'. And unsubscribing will work like 'removeEventListener'. Actually, underneath, RxJS will use those methods for us.


### Filter Operator
```
interface newsFeed {
  category: 'Business' | 'Sports';
  content: string;
}

const newsFeed$ = new Observable<newsFeed>((subscriber) => {
  setTimeout(
    () => subscriber.next({ category: 'Business', content: 'A' }),
    1000
  ),
    setTimeout(
      () => subscriber.next({ category: 'Sports', content: 'B' }),
      3000
    ),
    setTimeout(
      () => subscriber.next({ category: 'Business', content: 'C' }),
      4000
    ),
    setTimeout(
      () => subscriber.next({ category: 'Sports', content: 'D' }),
      6000
    ),
    setTimeout(
      () => subscriber.next({ category: 'Business', content: 'E' }),
      7000
    ),
    setTimeout(
      () => subscriber.next({ category: 'Business', content: 'F' }),
      9000
    );
});

// newsFeed$.pipe(
//   filter(item => item.category =='Sports')
// ).subscribe({
//   next: value => console.log(value)
// })

const sportsNewsFeed$ = newsFeed$.pipe(
  filter((item) => item.category == 'Sports')
);

const businessNewsFeed$ = newsFeed$.pipe(
  filter((item) => item.category == 'Business')
);

sportsNewsFeed$.subscribe({
  next: (value) => console.log(value),
});

```

So the 'pipe' method allows us to provide the Pipeable Operators we want to apply here and it will connect all these operators together and return the final output Observable with all these operators applied in the provided order so we can subscribe to it over here. So, we'll use a single 'filter' operator here. We need to import it from RxJS like this. And as an argument, we pass a callback which will be used to determine whether this value should be passed through or not.

### map

```
const randomFirstName$ = ajax<any>('https://random-data-api.com/api/name/random_name').pipe(
  map(ajaxResponse => ajaxResponse.response.first_name)
);

const randomCapital$ = ajax<any>('https://random-data-api.com/api/nation/random_nation').pipe(
  map(ajaxResponse => ajaxResponse.response.capital)
);

const randomDish$ = ajax<any>('https://random-data-api.com/api/food/random_food').pipe(
  map(ajaxResponse => ajaxResponse.response.dish)
);

forkJoin([randomFirstName$, randomCapital$, randomDish$]).subscribe(
  ([firstName, capital, dish]) =>
    console.log(`${firstName} is from ${capital} and likes to eat ${dish}.`)
);

randomFirstName$.subscribe(value => console.log(value));

randomCapital$.subscribe(value => console.log(value));

randomDish$.subscribe(value => console.log(value));


```

### tap
In the coding section, we'll use the 'tap' operator to watch what's happening at every stage of our pipeline of operators. This is useful for debugging when you have a few operators stacked and you'd like to see what values are emitted somewhere in the middle. So we'll start by creating an Observable which will emit some numbers. Then, we'll use the 'filter' and 'map' operators so we have a couple of operators stacked. Finally, we'll use the 'tap' operator to console log what's happening.

```
of(1,2,4,6,8,10).pipe(
  tap(value => console.log("Spy =>", value)),
  map(item => item *2),
  filter(item => item>5)
).subscribe( value => console.log("Output =>",value));

```

https://jaywoz.medium.com/information-is-king-tap-how-to-console-log-in-rxjs-7fc09db0ad5a


### debounceTime
How can we use the 'debounceTime' operator to wait for the emissions to settle down before emitting the final value.

```
const sliderInput = document.querySelector('input#slider');

fromEvent(sliderInput, 'input').pipe(
  debounceTime(2000),
  map(event => event.target['value'])
).subscribe(value => console.log(value));

```

### catchError

This operator is interested in the error notifications only. 'catchError' allows us to provide a fallback Observable which will be used in case the original source emits an error. If that would happen the catchError's logic would not reemit that error, but subscribe to the provided fallback Observable instead. And all notifications received by this new inner Subscription will be passed to the output.

```
const failingHttpRequest$ = new Observable(subscriber => {
  setTimeout(() => {
    subscriber.error(new Error('Timeout'));
  }, 3000);
});

console.log('App started');

failingHttpRequest$.pipe(
    catchError(error => of('Fallback Error'))
  ).subscribe({
    next: value => console.log(value),
    complete: () => console.log('Completed')
  });

```

And sometimes we don't want to provide any fallback value if something fails, but, instead, we would like to just catch the error and not show anything.

```
failingHttpRequest$.pipe(
  catchError(error => EMPTY)
).subscribe({
  next: value => console.log(value),
  complete: () => console.log('Completed')
});
```

Before having a look at another popular use of 'catchError', let's introduce a built-in Observable provided by RxJS. It's called 'EMPTY' and this Observable is empty, as it says. So once you subscribe to it, it doesn't emit any values. It will immediately complete instead. This is useful if you would like to hide the error notification from your Observer, but don't want to provide any fallback values.













