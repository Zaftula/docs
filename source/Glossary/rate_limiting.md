---
seo:
  title: Rate Limiting
  description: Rate limiting happens when a recipient mail server doesn't allow emails to be delivered at the same rate as they were sent.
  keywords: rate limiting, throttling
title: Rate Limiting
weight: 0
layout: page
navigation:
  show: false
---

There are limitations to delivery rates imposed by recipient mail servers. Exceeding these limitations results in a practice
referred to as [throttling]({{root_url}}/Glossary/throttling.html). Throttling in terms of email means that a recipient mail server has accepted all the mail it is
willing to accept from your IP for a certain period of time.

{% info %} Reminder: If you have not yet completed the [account verification steps](https://app.sendgrid.com/guide) for your SendGrid account, you will only be able to send 100 emails per day. {% endinfo %}

Please visit our [pricing page]({{site.pricing_url}}?mc=SendGrid%20Documentation) to see the account specific sending limits.
