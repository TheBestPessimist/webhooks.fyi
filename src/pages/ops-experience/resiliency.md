---
title: Heartbeat, Queueing, and Circuit Breaking
description: Resiliency Controls
--- 


[comment]: <TODO: @sudobinbash: add good examples we found. Future: Break sections into categories>

Webhook listeners — like any other piece of software — will eventually become unstable or unavailable due to network or system issues. Good webhook providers recognize **availability as an inevitable problem** and provide resiliency features to reduce the burden on webhook consumers. Examples of interesting features include:

- **Heartbeat checks**: Webhook providers reach out to the listeners regularly to check their status. If a listener is not available, the provider takes action — like queueing notifications or sending alerts to system admins — until the webhook listener is fixed. This feature is helpful especially in webhooks that don't send notifications often.

- **Queueing**: webhook providers can keep track of historical information of webhook events sent and allow consumers to send messages again after failures or unavailability. Queues can be implemented on listener errors or in conjunction with heartbeat checks.

- Some webhook providers implement **Circuit Breaking** logic to throttle and aleviate requests to webhook listeners when webhook requests cross a error or response time threshold.

These features help consumers keep their service resilient and recover from issues faster and without message loss. 
