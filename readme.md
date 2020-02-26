Octany API
==========

Looking to integrate with Octany? We've got everything you need here.


Where do I start?
-----------------

Want to get started with Widget integration?

1. [Widget examples](widgets/examples.md)

Want to get started with API integration? Here's a quick check list:

1. [Get your API token](#authentication)
2. Access data via our [endpoints](#endpoints)
3. Subscribe to our [webhooks](#webhooks) 
4. Have a question? [Send us an email](mailto:support@octany.com)

Authentication
--------------

Generate your API token by logging in to [Octany](https://app.octany.com) and you'll find 
API tokens in `Settings`.

When making an API call, add your token as a `X-API-Key` header. Example cURL call:

```
curl "https://app.octany.com/api/[ACCOUNT_ID]/subscriptions" \
     -H 'X-API-Key: [TOKEN]'
```

Replace `[ACCOUNT ID]` with your Octany account id and `[TOKEN]` with your API token.
 

Endpoints
---------

- [Customers](endpoints/customers.md)
- [Subscriptions](endpoints/subscriptions.md)

Webhooks
--------
 
- [subscription.created](webhooks/webhooks.md#subscriptioncreated)
- [subscription.renewed](webhooks/webhooks.md#subscriptionrenewed)
- [subscription.cancelled](webhooks/webhooks.md#subscriptioncancelled)
- [order.paid](webhooks/webhooks.md#orderpaid)