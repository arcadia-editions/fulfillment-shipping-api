# Fulfillment Shipping

## Description

Fulfillment Shipping is the bounded context that owns the operational step after
an order is commercially confirmed. It schedules fulfillment, decides whether
shipping can proceed, and moves the order toward physical delivery readiness.

It represents the operational side of the flow after the commercial sale has
already been confirmed.

## Scope

- Schedule fulfillment after an order is confirmed
- Hold shipping address and item-level fulfillment data needed for execution
- Decide whether the shipment is ready to proceed or has failed
- Publish shipping outcomes used by payment capture and downstream operations

## Main domain elements

- `Fulfillment`: aggregate for shipment scheduling and readiness
- `FulfillmentShippingService`: commands for scheduling and preparing shipments
- `FulfillmentScheduled`: event announcing shipping work has been scheduled
- `FulfillmentFailed`: event announcing fulfillment could not proceed
- `FulfillmentReadyToShip`: event announcing the order is ready for shipment
