# `git4ol` Events

`git4ol-events` provide services for generating and consuming events.

Underneath the hood `git4ol-events` will be driven by [ReactiveX](http://reactivex.io/) sprinkled [EventEmitters](https://nodejs.org/api/events.html) so events are asynchronous and support composition (what we have in mind is something like [this](https://github.com/Reactive-Extensions/RxJS/blob/master/doc/howdoi/eventemitter.md)).

From the outside `git4ol-events` will provide [webhooks](https://en.wikipedia.org/wiki/Webhook) for event subscription and consumption.