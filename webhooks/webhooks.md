Subscription Webhooks
=====================

To receive webhooks, go into `Settings` and add an endpoint. 
To explore and test webhooks we recommend using a tool such as [Requestbin](https://requestbin.com/) or [Ngrok](http://ngrok.io/) on your local development machine.

All webhooks are sent as POST requests with a JSON body to your endpoint. Please check the `name` attribute to see what kind of event it is.

Events:

- [subscription.created](#subscriptioncreated)
- [subscription.renewed](#subscriptionrenewed)
- [subscription.cancelled](#subscriptioncancelled)
- [order.paid](#orderpaid)

Security
--------------------

Each webhook we send contains a header called `Octany-Signature` which contains the hash of the payload. It's using [HMAC](https://en.wikipedia.org/wiki/HMAC) with a unique secret for your endpoint. You can match the payload with your secret against the signature in the header to validate the request.

Customer vs Billing
--------------------
We've introduced a new way to interact with people and companies. Instead of the generic customer object, we now have separate company and person objects that are associated with each billing_method.

We recommend storing customer data like name, email, and phone number from the data in `billing_method`.

It's important to note that this update is 100% backward compatible. While the customer object is still around, it's marked as deprecated. For a smoother transition to newer API versions, we suggest not using the deprecated customer object.

subscription.created
--------------------

This event is sent when a new subscription has been created in the system.

###### Example JSON Payload

```json
{
    "id": "59958608-8e4d-4795-b7b6-91512359c935",
    "name": "subscription.created",
    "account": 1421,
    "created_at": "2023-10-20T09:01:43+00:00",
    "data": {
        "id": 70212202,
        "vat": 2500,
        "price": 34900,
        "status": "active",
        "ends_at": null,
        "product": {
            "id": 1225,
            "name": "Pro",
            "type": "month",
            "price": 34900,
            "currency": "sek",
            "vat_rate": 2500
        },
        "currency": "sek",
        "customer": {
            "id": 452512733,
            "name": "John Doe",
            "type": "company",
            "created_at": "2023-10-20T09:01:43+00:00",
            "updated_at": "2023-10-20T09:01:43+00:00",
            "vat_number": null,
            "archived_at": null
        },
        "renews_at": "2023-10-20T09:01:43+00:00",
        "customer_id": 452512733,
        "billing_method": {
            "name": "faktura",
            "type": "fortnox",
            "email": "invoice@example.com",
            "person": {
                "email": "john@example.com",
                "phone": false,
                "locale": "sv",
                "last_name": "Persson",
                "first_name": "Peter",
                "personal_identity_number": null
            },
            "address": {
                "zip": "116 53",
                "city": "Stockholm",
                "line1": "Sveavägen 11",
                "line2": null,
                "country": "SE",
                "created_at": "2023-10-20T09:01:43+00:00",
                "updated_at": "2023-10-20T09:01:43+00:00"
            },
            "company": {
                "name": "Example Company",
                "vat_number": "SE556742219001"
            }
        },
        "reference_id": null,
        "reference_name": null
    }
}
```

subscription.renewed
--------------------

Send every time a renewal of the subscription has been made. 
Includes the exact same payload as `subscription.created`

subscription.cancelled
----------------------

When a subscription has been cancelled. 
Please note that this event happens whenever a user or admin cancel the subscription. 
There might still be time left on the subscription before it ends. 

###### Example 

Jane signs up on February 14 and her subscription will renew on the 14th every month.
She cancels her subscription on July 24 and this will trigger the `subscription.cancelled` webhook.
In the payload you'll see that `ends_at` is August 14 and that `renews_at` is `null` since the subscription won't renew.
 
Includes the exact same payload as `subscription.created`

order.paid
----------

This event is sent for single and recurring payments made trough Octany. 
The event will be sent immediately for `card` and `Swish` payments. 
For `invoice` payments it will be sent as soon as the invoice has been created (usually within an hour)

###### Example JSON Payload

```json
{
  "id": "114d8fd9-862a-4832-a8d1-422bf4a778a7",
  "name": "order.paid",
  "account": 1421,
  "created_at": "2023-10-20T09:01:43+00:00",
  "data": {
    "id": 193468423,
    "customer_id": 449739128,
    "total": 34900,
    "total_with_vat": 43625,
    "currency": "sek",
    "reference_id": null,
    "reference_name": null,
    "state": "paid",
    "billing_method": {
      "name": "Swish",
      "type": "swish",
      "email": "jane@example.com",
      "person": {
          "email": "jane@example.com",
          "phone": "46730401224",
          "locale": "sv",
          "last_name": "Doe",
          "first_name": "Jane",
          "personal_identity_number": null
      },
      "address": null,
      "company": null
    },
    "items": [
      {
        "description": "Snowfire Website",
        "quantity": "1",
        "price": 34900,
        "vat": 2500,
        "product": {
          "id": 1225,
          "name": "Snowfire Website",
          "type": "month",
          "price": 34900,
          "currency": "sek",
          "vat_rate": 2500
        }
      }
    ],
    "customer": {
      "id": 449739128,
      "name": "Jane Doe",
      "type": "person",
      "vat_number": null,
      "archived_at": null
    }
  }
}
``` 
