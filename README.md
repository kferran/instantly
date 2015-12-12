instantly
======

What is this?
------
[EventSource](https://developer.mozilla.org/en-US/docs/Web/API/EventSource) abstraction layer. <br>
The EventSource API is easy as is. Reason I created this was to hide all logic I use when I implement EventSource. <br>
IMPORTANT. This is NOT EventSource Polyfill!

Installation
------
It's available on npm.
```
npm install --save instantly
```

How can I use this library?
------
It's a UMD module. If you don't know what UMD is: [https://github.com/umdjs/umd](https://github.com/umdjs/umd)

Usage
------
```javascript
// Example
var es = new Instantly('http://your-sse-endpoint.codes/channel', {
    retries: 2, // Optional. Default: 5 retries if connection to your endpoint fails.
    timeout: 1000, // Optional. Default: 15 seconds (15000). This is how often we should do a retry
    error: function() {} // Optional. Extending the internal error handler
});

// If you want to use default options
// var es = new Instantly('http://your-sse-endpoint.codes/channel');

// Listen to messages without any event set
es.on('message', function newMessage(msg) {
    console.log(msg.data);
});

// Listen to messages with an event set
es.on('eventName', function newMessage(msg) {
    console.log(msg.data);
});

// Start to listen for events send by SSE
es.listen();
```

Contribution
------
Contributions are appreciated.

License
------
MIT-licensed. See LICENSE.
