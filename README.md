# REST Gateway Notification Action

Sends out a notification via REST-Gateway.

# Usage


## Secrets

* `NOTIFICATIONS_DEFAULT_RECIPIENT` - Notifications recipient (currently a telegram chat)
* `REST_GATEWAY_API_URL` - URL to your REST-Gateway instance
* `REST_GATEWAY_TOKEN` - Authentication token to your REST-Gateway instance
* `REST_GATEWAY_BOT_NAME` - Bot name your token dedicated to

## Outputs


# Example

```yaml
---
name: Workflow

on:
  push:
    branches:
      - "*"

jobs:
  real_actual_job:
    name: Real Actual Jon
    runs-on: ubuntu-latest

    steps:

      - name: Check out code
        uses: actions/checkout@v2
        with:
          fetch-depth: 0

      - name: Send out notification about workflow
        uses: rest-gateway/notification-action@master
        with:
          message: "Workflow happened!"
          recipient: "${{ secrets.NOTIFICATIONS_DEFAULT_RECIPIENT }}"
          rest_gateway_url: "${{ secrets.REST_GATEWAY_API_URL }}"
          rest_gateway_token: "${{ secrets.REST_GATEWAY_TOKEN }}"
          rest_gateway_bot_name: "${{ secrets.REST_GATEWAY_BOT_NAME }}"

```