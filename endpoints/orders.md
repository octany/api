Orders
======

Endpoints:

- [Get an order](#get-an-order)

Get an order
------------

* `GET /order/193468423`

###### Example JSON Response

```json
{
  "status": 200,
  "success": true,
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
      "email": "jane@snowfire.net",
      "type": "swish"
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
      "archived_at": null,
      "person": {
        "first_name": "Jane",
        "last_name": "Doe",
        "email": "jane@snowfire.net",
        "phone": null,
        "locale": "sv"
      },
      "address": null
    }
  }
}
``` 