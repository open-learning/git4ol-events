# `git4ol` Events

`git4ol-events` provide services for generating and consuming events.

Underneath the hood `git4ol-events` will be driven by [ReactiveX](http://reactivex.io/) sprinkled [EventEmitters](https://nodejs.org/api/events.html) so events are asynchronous and support composition (what we have in mind is something like [this](https://github.com/Reactive-Extensions/RxJS/blob/master/doc/howdoi/eventemitter.md)).


## Consumption

From the outside `git4ol-events` will provide [webhooks](https://en.wikipedia.org/wiki/Webhook) for event consumption.

## Generation

All events (`git4ol` internal or external) should be generated using POST with a JSON payload as the body:

```
POST http://server/git4ol-events/trigger/event.name
{
  "property": "value"
}
```

The default is to keep the connection open and respond with the collected result when the last handler completes.

```
{
  "result": "value"
}
```

An alternative is to provide a `callback` parameter in which case the response will be a callback ID and the URL provided will be called using a POST with the collected result as the body and the callback ID as a parameter when the last handler completes:


```
POST http://server/git4ol-events/trigger/event.name?callback=http://other_server/handler
```

```
12345
```

```
POST http://other_server/handler?id=12345
{
  "result": "value"
}
```