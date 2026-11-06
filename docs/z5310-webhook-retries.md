# Webhook delivery retries

Our platform delivers webhook events to the URL you configure in the dashboard. This guide explains how retries work.

## Retry schedule

If your endpoint does not return a 2xx status within 10 seconds, we retry the delivery up to 5 times with exponential backoff: 1 minute, 5 minutes, 30 minutes, 2 hours and 12 hours.

## Idempotency

Every event carries a unique `event_id`. Store it and ignore duplicates, because a retry can arrive after a slow success.

## Disabling an endpoint

After 5 failed retries the endpoint is marked as failing and you receive an email. Fix the endpoint and re-enable it from the Webhooks settings page.
