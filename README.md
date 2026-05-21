# fulfillment-shipping-api

Fulfillment Shipping is the bounded context that owns the operational step after
an order is commercially confirmed. It schedules fulfillment, determines whether
shipping can proceed, and publishes the operational outcomes needed by the rest of
the platform.

In the architecture article, `OrderConfirmed` is the pivotal event where language
shifts from commercial intent to operational work. This repository represents that
operational shipping boundary.

## Bounded context scope

- Schedule fulfillment after an order is confirmed
- Hold shipping address and item-level fulfillment details needed for execution
- Decide whether the shipment is ready to proceed or has failed
- Publish shipping outcomes for payment capture and downstream operations

This service does not own checkout, payment authorization, or customer messaging.
It owns the shipping workflow itself.

## Contents

- `domain-model.zdl`: source of truth for the fulfillment aggregate, lifecycle, commands, and events
- `README.md`: repository overview and bounded-context explanation

## Main domain elements

- `Fulfillment`: aggregate for shipment scheduling and readiness
- `FulfillmentShippingService`: commands for scheduling and preparing shipments
- `FulfillmentScheduled`, `FulfillmentFailed`, `FulfillmentReadyToShip`: operational shipping events
