Products
========

Endpoints:

- [Get products](#get-products)
- [Get a product](#get-a-product)

Get products
------------

* `GET /products` will returned a paginated list of all products

###### Example JSON Response

```json
{
  "status": 200,
  "success": true,
  "data": [
    {
      "id": 4662,
      "name": "Base"
      "price": 49900,
      "currency": "sek",
      "vat_rate": 2500,
      "interval": "month",
    },
    {
      "id": 4663,
      "name": "Pro"
      "price": 79900,
      "currency": "sek",
      "vat_rate": 2500,
      "interval": "month",
    },
  ],
  "pagination": {
    "count": 2,
    "total": 2,
    "perPage": 50,
    "currentPage": 1,
    "totalPages": 1,
    "links": []
  }
}
```

Get a product
-------------

* `GET /product/4663`

###### Example JSON Response

```json
{
  "status": 200,
  "success": true,
  "data": {
      "id": 4663,
      "name": "Pro"
      "type": "recurring_donation",
      "price": 79900,
      "currency": "sek",
      "vat_rate": 2500,
      "interval": "month",
  }
}
``` 
