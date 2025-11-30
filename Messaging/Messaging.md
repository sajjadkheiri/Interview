# Messaging

## RabbitMQ

### What is Dead letter exchange

Dead Letter Exchange in RabbitMQ is a special exchange where messages go when they $\textsf{\color{#fbbc05}{cannot be delivered or processed}}$, for example after they are rejected or $\textsf{\color{#fbbc05}{retried too many times}}$.

**ex :**  An order service reads messages from a queue. If processing fails three times, the message is sent to a Dead Letter Exchange and stored in a dead letter queue so the team can inspect or reprocess bad orders later.

## Kafka