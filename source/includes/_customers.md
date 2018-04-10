# Customers

## Create a Customer

> Sample Request:

```shell
curl -u private-api-key: https://api.paymentspring.com/api/v1/customers
-d company="ABC Corp"
-d first_name="John"
-d last_name="Doe"
-d address_1="123 Apple Street"
-d address_2="Apt 101"
-d city="Lincoln"
-d state="NE"
-d zip="68521"
-d phone="402-437-0127"
-d fax="402-437-0100"
-d website="http://www.example.com"
-d card_number="4111111111111111"
-d card_exp_month="1"
-d card_exp_year="2020"
-d country="USA"
-d email="test@example.com"
```


> Expected Response Data:

```json
{
    "id": "95c129",
    "created_at": "2017-11-20T19:12:20Z",
    "updated_at": "2017-11-20T19:12:20Z",
    "class": "customer",
    "card_owner_name": null,
    "address_1": "123 Apple Street",
    "address_2": "Apt 101",
    "company": "ABC Corp",
    "country": "USA",
    "fax": "402-4370-0100",
    "first_name": "John",
    "last_name": "Doe",
    "email": "test@example.com",
    "city": "Lincoln",
    "phone": "402-437-0127",
    "zip": "68521",
    "state": "NE",
    "website": "http://www.example.com",
    "card_type": "visa",
    "last_4": "1111",
    "card_exp_month": 1,
    "card_exp_year": 2020,
    "default_receipts": false,
    "default_receipt_template_id": null,
    "bank_account_number_last_4": null,
    "bank_routing_number": null,
    "bank_account_holder_first_name": null,
    "bank_account_holder_last_name": null,
    "bank_account_type": null,
    "default_method_id": "15f219d37b5f4aabb8cdc5fa2a143e43",
    "methods": [
        {
            "id": "ad77af999677462e83266e5b55cff340",
            "class": "payment_method",
            "method_type": "bank_account",
            "bank_account_number_last_4": null,
            "bank_routing_number": null,
            "bank_account_holder_first_name": null,
            "bank_account_holder_last_name": null,
            "bank_account_type": null,
            "customer_id": null,
            "created_at": "2017-11-20T19:12:20.546Z",
            "updated_at": "2017-11-20T19:12:20.563Z",
            "company": "ABC Corp",
            "address": {
                "address_1": "123 Apple Street",
                "address_2": "Apt 101",
                "city": "Lincoln",
                "state": "NE",
                "country": "USA",
                "zip": "68521",
                "company": "ABC Corp"
            }
        },
        {
            "id": "15f219d37b5f4aabb8cdc5fa2a143e43",
            "class": "payment_method",
            "method_type": "credit_card",
            "last_4": "1111",
            "card_type": "visa",
            "card_exp_month": "1",
            "card_exp_year": "2020",
            "card_owner_name": null,
            "customer_id": null,
            "created_at": "2017-11-20T19:12:20.503Z",
            "updated_at": "2017-11-20T19:12:20.531Z",
            "address": {
                "address_1": "123 Apple Street",
                "address_2": "Apt 101",
                "city": "Lincoln",
                "state": "NE",
                "country": "USA",
                "zip": "68521",
                "company": "ABC Corp"
            }
        }
    ]
}
```

### POST /customers

Create and store a customer with payment information.

### Parameters

Parameter | Details
--------- | -----------
username | This request expects a merchant’s private API key to be provided as the username with a blank password. A public API key can not be used for this type of request.
company | Name of company to be saved on the record.


## Delete a Customers

> Sample Request:

```shell
curl -u private-api-key:
https://api.paymentspring.com/api/v1/customers/62a987ed39
```

> Expected Response Data:

```json
{
    "success": true
}
```

### DELETE /customers

Delete a customer by using their ID number.

### Parameters

Parameter | Details
--------- | -----------
username | This request expects a merchant’s private API key to be provided as the username with a blank password. A public API key can not be used for this type of request.
id | ID of the customer to delete.
