# Reactive or Non-Blocking
## Buildling Concept
- operations that a thread dosen't wait for to complete
  - fetching data from network
  - reading from a file
- how it gets notfied
  - callback : another function's argument
  - promise/futures : an object representing like the result of asyncronous network call and can be chanied for actions
  - reactive streams : Observables and Observers
  - event listener
``` console
The callback is invoked, or the promise is resolved, or the observable emits data after the network request completes.
When the data arrives, the registered handler (callback, .then(), or subscription) runs the logic for handling that data.
```

## Tomcat VS Netty
- Tomcat
  - blocking servlet container
  - thread per request model
  - when controller method returns reactive objects, Spring framekwork allows the thread to be released back to the thread pool to handle other reuqests. Once the reactive object is completed asyncronously, a new thread from tomcat's thread pool generates responses
- Netty
  - no thread-per-request model
  - event-driven : event loop
- Both
  - TCP socket remains open until the response is fully sent back to the client unless HTTP keep-alive is in use
  - The TCP connection is just idle during the entire asynchronous operation
