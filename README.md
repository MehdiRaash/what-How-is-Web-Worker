# What and How is Web Worker

## preface

JavaScript is single threaded which the host environment(for example a browser) provides and manages the thread. so all the code and tasks like timers, Ajax, UI events and etc run on the main thread.

If you have processing-intensive tasks but you don't want them to run on the main thread (which may slow down the browser/UI), you might have wished that JavaScript could operate in a multithreaded manner.

"Web worker" is an option to not just stand on the main thread, so it's all about performance every where in computing devices, also in web browsers.

## What is Web Worker and what it brings up?

Web Workers is a simple means for web content to run scripts in background threads,( another thread ).
Let's call that thread **the worker thread** , the worker thread can perform tasks without interfering with the user interface tasks which runs on main thread.

A worker is an object created using a constructor (e.g. Worker()) that runs a named JavaScript file — this file contains the code that will run in the worker thread; workers run in another global context that is different from the current window. Thus, using the window shortcut to get the current global scope (instead of self) within a Worker will return an error.

Hence, they can perform I/O using XMLHttpRequest (although the responseXML and channel attributes are always null). Once created, a worker can send messages to the JavaScript code that created it by posting messages to an event handler specified by that code (and vice versa.)

### Important notes 

- Web Worker is a feature of the browser (also known as: host environment) and actually has almost nothing to do with the JavaScript language itself. That is, JavaScript does not *currently* have any features that support threaded execution.

- Workers may, in turn, **spawn new workers**, as long as those workers are hosted within the same origin as the parent page.

- You can run whatever code you like inside the worker thread, with some exceptions. For example, you can't directly manipulate the DOM from inside a worker, or use some default methods and properties of the window object. But you can use a large number of items available under window, including WebSockets, and data storage mechanisms like IndexedDB and the Firefox OS-only Data Store API.

- Data is sent between workers and the main thread via a system of messages — both sides send their messages using the `postMessage()` method, and respond to messages via the onmessage event handler (the message is contained within the Message event's data attribute.) The data is copied rather than shared.

### Dedicated workers

A dedicated worker is only accessible by the script that called it. 

### Shared Workers

A shared worker is accessible by multiple scripts, even if they are being accessed by different windows, iframes or even workers.
