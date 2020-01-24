Customers
=========

Endpoints:

- [Get customers](#get-customers)
- [Get a customer](#get-a-customer)

Get customers
-----------------

* `GET /customers` will returned a paginated list of all customers

###### Example JSON Response

```json
{
  "status": 200,
  "success": true,
  "data": [
    {
      "id": 247973935,
      "name": "John Doe",
      "type": "person",
      "vat_number": null,
      "person": {
        "first_name": "John",
        "last_name": "Doe",
        "email": "john@octany.com",
        "phone": null,
        "locale": "sv"
      },
      "address": {
        "line1": "Kungsgatan 25",
        "line2": "",
        "zip": "114 50",
        "city": "Stockholm",
        "country": "SE"
      }
    }
  ],
  "pagination": {
    "count": 1,
    "total": 1,
    "perPage": 20,
    "currentPage": 1,
    "totalPages": 1,
    "links": []
  }
}
```

Get a customer
--------------

* `GET /customer/247973935`

###### Example JSON Response

```json
{
  "status": 200,
  "success": true,
  "data": {
    "id": 247973935,
    "name": "John Doe",
    "type": "person",
    "vat_number": null,
    "person": {
      "first_name": "John",
      "last_name": "Doe",
      "email": "john@octany.com",
      "phone": null,
      "locale": "sv"
    }
  }
}
``` 