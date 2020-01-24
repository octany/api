Subscriptions
=============

Endpoints:

- [Get subscriptions](#get-subscriptions)
- [Get a subscription](#get-a-subscription)

Get subscriptions
-----------------

* `GET /subscriptions` will returned a paginated list of all subscriptions

_Optional filters_

* `reference_id` will only return subscriptions with a specific reference id

###### Example JSON Response

```json
{
  "status": 200,
  "success": true,
  "data": [
    {
      "id": 29281116,
      "customer_id": 15831253
    },
    {
      "id": 24381116,
      "customer_id": 23831253
    }
  ],
  "pagination": {
    "count": 20,
    "total": 27,
    "perPage": 20,
    "currentPage": 1,
    "totalPages": 2,
    "links": []
  }
}
```

Get a subscription
------------------

* `GET /subscription/29281116`

###### Example JSON Response

```json
{
  "status": 200,
  "success": true,
  "data": {
    "id": 29281116,
    "customer_id": 15831253,
    "price": 29900,
    "vat": 2500,
    "currency": "sek",
    "renews_at": "2020-01-06T14:55:33+00:00",
    "ends_at": null,
    "reference_id": "102676",
    "reference_name": "",
    "status": "active",
    "billing_method": {
      "email": "invoice@octany.com",
      "type": "stripe"
    },
    "product": {
      "name": "Base",
      "type": "month",
      "price": 29900,
      "currency": "sek",
      "vat_rate": 2500
    }
  }
}
``` 