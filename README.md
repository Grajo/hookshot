# Hookshot

A webhook delivery service built with Ruby on Rails, Postgres and Sidekiq.

## The problem

Notifying third party systems with a plain HTTP request fails in many ways: the destination is down, slow or returns an error, and the event is lost. Retrying naively can deliver the same event twice.

## What it will do

* Accept events and store them durably in Postgres
* Deliver them to registered endpoints through Sidekiq jobs
* Retry failed deliveries with exponential backoff
* Sign every payload with HMAC so receivers can verify the sender
* Include a stable event id so receivers can deduplicate

Delivery is at least once. Idempotency on the receiving side is made possible by the event id.

## Status

Early stage. Only synthetic test data is used.

## License

MIT