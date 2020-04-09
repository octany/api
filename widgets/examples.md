Widget examples
===============

We recommend using the following CSS code for all widgets

```css
.octany-wrapper {
    text-align: center;
    margin: 0 auto;
    width: 100%;
    max-width: 600px;
    border: 0px solid #D5D8DF;
}
```

Donation Widget
---------------

This widget is for donations

```html
<div class="octany-wrapper">   
    <div class="octany-wrapper">   
        <octany-widget
            url="https://app.octany.com"
            account-id="[ACCOUNT_ID]"
            product-id="[PRODUCT_ID_1]|[PRODUCT_ID_2]"
            tab-title="Bli månadsgivare|Engångsgåva"
            page-title="Ge en gåva varje månad|Ge en engångsgåva"
            type="iframe"
            locale="sv"
        ></octany-widget>

        <link rel="stylesheet" href="https://app.octany.com/1427/checkout/appearance">
        <script src="https://app.octany.com/js/checkout.js"></script>
    </div>
</div>
```

Button Widget
-------------

This widget works with subscriptions and donations

```html
<octany-widget
    url="https://app.octany.com"
    account-id="[ACCOUNT_ID]"
    product-id="[PRODUCT_ID]"
    type="button"
    locale="sv"
    label="Subscribe"
    price-with-vat="false"
></octany-widget>
```

Properties
----------

Here is a list of all properties

* `url` The URL to Octany (required)
* `account-id` Your specific Octany account id
* `product-id` The product you want to use. We support two values for the donation widget separated by a pipe character (example: 1422|1423)
* `type` button or iframe
* `locale` We support English (en) and Swedish (sv)
* `success-url` Customers are sent to this URL when the payment has been completed
* `abort-url` Customers are sent to this URL if they close Octany without making a purchase
* `reference-id` A custom string which is sent back to your application when using Webhooks or an API endpoint, max 250 characters
* `reference-name` Works exactly like reference-id, but the name is also visible in the Octany UI
* `price-with-vat` Set this to true if you want to display price with VAT included, defaults to false (type="button" only)
* `amount` Set a custom amount (type="button" only)
* `first-name` Prefill first name
* `last-name` Prefill last name
* `email` Prefill email 
* `phone` Prefill phone number (Must be prefixed with tel:, example: `tel:0701234567`) and is only used for Swish payments
* `company` Check 'pay as company' and prefill company name
