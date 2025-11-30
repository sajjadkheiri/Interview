# API

## What is JWT

## Patch vs Put
**PUT** $\textsf{\color{#fbbc05}{replaces}}$ the entire resource, while **PATCH** applies partial $\textsf{\color{#fbbc05}{modifications}}$.

## what is the Idempotency

Calling the same operation many times has the same effect as calling it once. An operation is $\textsf{\color{#fbbc05}{idempotent}}$ if running it $\textsf{\color{#fbbc05}{once or many times has the same effect}}$ on the system.
  

![Http-Idempotent](/Resources/Idempotency.png)



**ex:** a payment API that safely ignores duplicate charge requests, so if the client sends the same request three times, the customer is charged only one time.


## what is the Resilience

Ability of a system to keep working or degrade gracefully when parts fail or are slow.

**ex:** a service that uses timeouts, retries with backoff, and a circuit breaker so a slow database or external API does not bring the whole system down.

## How idempotency and resilience work together : 

They’re tightly coupled:
- Retries (resilience) need idempotency to be safe.
- At-least-once delivery (messaging resilience) needs idempotent handlers.

- Circuit breakers and timeouts cause failures that will be retried or re-queued; without idempotency, those duplicates change business state.


So usually the flow is:
1. Design business operations to be idempotent.
2. Then safely add:

    - Retries
    - At-least-once message processing
    - Circuit breakers
    - Queue-based asynchronous workflows


## what is Circuit-Breaker

Circuit breaker is a $\textsf{\color{#fbbc05}{resilience pattern}}$ that stops your service from repeatedly calling a failing dependency by opening the circuit after many errors and then retrying after a pause.

**ex :** a payment service that consumes messages from RabbitMQ and calls a bank API can use a circuit breaker so if the bank is down it fails fast and moves the message to retry or a dead letter queue instead of hanging.