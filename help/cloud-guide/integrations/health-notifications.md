---
title: Health notifications
description: Learn how to configure Slack, email, and PagerDuty notifications for disk space usage on your Adobe Commerce on cloud infrastructure project.
feature: Cloud, Observability, Integration
exl-id: d3173098-78ed-42a8-aeb3-9ccbaccc4d32
---
# Health notifications

Adobe Commerce on cloud infrastructure monitors disk space usage on all applications and services in your Starter environment or your Pro Integration environment. A database disk that runs out of space could cause data corruption. The health status check occurs every 5 minutes and can notify you by email or other external service. There are three low-disk warnings for health notifications:

-  **Warning**—available disk space drops below 20%
-  **Critical**—available disk space drops below 10%
-  **All-clear**—available disk space returns above 20%, after a low-disk event

>[!NOTE]
>
>On Pro Production environments, you can use the Managed alerts for Adobe Commerce alert policy for New Relic to monitor disk space. See [Monitor performance with Managed Alerts](../monitor/new-relic.md#monitor-performance-with-managed-alerts).

## Email notifications

The health email integration requires an origination address and at least one recipient address. You can use the same email address for the `from-address` and the `recipients` address. The following example registers a health email integration with two recipients:

```bash
magento-cloud integration:add --type health.email --from-address you@example.com --recipients them@example.com --recipients others@example.com
```

## Slack channel notifications

Slack is an external service that uses interactive apps called bots to post messages in a chat room. Before you can receive health notifications in Slack, you must create a custom [bot user](https://api.slack.com/bot-users) for your Slack group. After you configure the bot user for your channel, or channels, save the [bot token](https://api.slack.com/docs/token-types#bot) provided by Slack to register your integration. The following example registers health notifications in a Slack channel:

```bash
magento-cloud integration:add --type health.slack --token SLACK_BOT_TOKEN --channel '#slack-channel-name'
```

## PagerDuty notifications

PagerDuty is an external service that can notify on-call team members of important issues. Before you can receive health notifications in PagerDuty, you must create a [PagerDuty integration](https://developer.pagerduty.com/v2/docs/integrating) that uses the Events API version 2. Use the Integration Key, or _routing key_, to register your integration. The following example registers notifications for PagerDuty using a routing key:

```bash
magento-cloud integration:add --type health.pagerduty --routing-key PAGERDUTY_ROUTING_KEY
```
