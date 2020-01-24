Subscription Webhooks
=====================

To receive webhooks, go into `Settings` and add an endpoint. 
To explore and test webhooks we recommend using a tool such as [Requestbin](https://requestbin.com/) or [Ngrok](http://ngrok.io/) on your local development machine.

All webhooks are sent as POST requests with a JSON body to your endpoint. Please check the `name` attribute to see what kind of event it is.

Events:

- [subscription.created](#subscriptioncreated)
- [subscription.renewed](#subscriptionrenewed)
- [subscription.cancelled](#subscriptioncancelled)

subscription.created
--------------------

This event is sent when a new subscription has been created in the system.

###### Example JSON Payload

```json
{
    "id": "59958608-8e4d-4795-b7b6-91512359c935",
    "name": "subscription.created",
    "account": 1421,
    "created_at": "2020-01-17T15:07:57+00:00",
    "data": {
        "id": 70212202,
        "vat": 2500,
        "price": 34900,
        "status": "active",
        "ends_at": null,
        "product": {
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
            "type": "person",
            "person": {
                "first_name": "John",
                "last_name": "Doe",
                "email": "john@octany.com",
                "phone": null,
                "locale": "sv",
                "created_at": "2020-01-17T13:35:10+00:00",
                "updated_at": "2020-01-17T13:35:10+00:00"
            },
            "address": {
                "line1": "Kungsgatan 25",
                "line2": "",
                "zip": "114 50",
                "city": "Stockholm",
                "country": "SE",
                "created_at": "2020-01-17T13:35:14+00:00",
                "updated_at": "2020-01-17T13:35:14+00:00"
            },
            "created_at": "2020-01-17T13:29:59+00:00",
            "updated_at": "2020-01-17T13:30:09+00:00",
            "vat_number": null,
            "archived_at": null
        },
        "renews_at": "2020-02-17T13:35:14+00:00",
        "customer_id": 452512733,
        "billing_method": {
            "type": "fortnox",
            "email": "invoice@octany.com"
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