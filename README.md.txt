# Amazon SNS-SQS Fan-Out for Event Notifications

## Project Overview
This project demonstrates an event-driven notification system using Amazon Simple Notification Service (SNS) and Amazon Simple Queue Service (SQS).

SNS distributes a published event to multiple subscribed SQS queues, allowing different services to independently receive the same notification.

## Architecture
```text
                 Publisher
                     |
                     v
              SNS: OrderEvents
               /      |       \
              v       v        v
        Inventory   Shipping  Notification
          Queue      Queue       Queue
           SQS        SQS         SQS
```

## AWS Services Used
- **Amazon SNS:** Publishes and distributes event notifications.
- **Amazon SQS:** Stores messages in queues for independent retrieval.
- **AWS Academy Learner Lab:** Environment used for implementation.

## Implementation
1. Created an SNS Standard topic named `OrderEvents`.
2. Created three SQS Standard queues:
   - `InventoryQueue`
   - `ShippingQueue`
   - `NotificationQueue`
3. Subscribed all three queues to the SNS topic.
4. Published a sample `ORDER_PLACED` event.
5. Polled the queues and verified that the event was delivered to each queue.

## Sample Event
```json
{
  "eventType": "ORDER_PLACED",
  "orderId": "ORD1001",
  "customer": "Sai",
  "product": "Laptop",
  "quantity": 1,
  "status": "Confirmed"
}
```

## Verification
The published event was successfully delivered to all three subscribed SQS queues. The messages were inspected in the AWS Console to verify fan-out delivery.

## Project Scope
This implementation focuses on SNS topic creation, SQS queue creation, subscriptions, event publishing, and message delivery verification. Application-level message processing is outside the current scope.

## Repository Structure
- `docs/` – Architecture and implementation documentation
- `screenshots/` – AWS Console implementation evidence
- `presentation/` – Project presentation and team brief

## Team
Sai Sumit Panigrahi

## Platform
AWS Academy Learner Lab