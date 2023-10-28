# Reactive stream
Reactive Streams is an initiative to provide a standard for asynchronous stream processing with non-blocking back pressure.

- minimum set of interfaces, methods and protocols

specifications [here](https://github.com/reactive-streams/reactive-streams-jvm/blob/v1.0.4/README.md)

```mermaid
sequenceDiagram
    participant Subscriber as Subscriber
    participant Publisher as Publisher
    participant Subscription as Subscription
    Subscriber ->> Publisher: subscribe(Subscriber)
    Publisher->>Subscription: new Subscription()
    Publisher->>Subscriber: onSubscribe(Subscription)


    loop Until completed
        Subscriber->>Subscription: request(long)
        Subscription-->>Publisher: 
        alt 
            Publisher->>Subscriber: onNext(T t)
            Publisher->>Subscriber: onError(Throwable t)
        end
        alt cancel subscription
            Subscriber->>Subscription: cancel()
            Subscription-->>Publisher: 
        end        
    end
    Publisher->>Subscriber: onComplete()
```
