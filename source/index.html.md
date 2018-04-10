---
title: Slate Test API Docs

language_tabs: # must be one of https://git.io/vQNgJ
  - shell

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

includes:
  - customers
  - errors

search: true
---

# Introduction

Welcome to the Test API Docs for PaymentSpring, powered by Slate. Currently, the API Docs
are hosted [here](https://paymentspring.com/developers/).

# Authentication

> When using the REST API, the API key is accepted through the username in the HTTP basic auth credentials system. No HTTP basic auth password is required. For example, a curl command to the API might be:


```
$ curl -u private-api-key: -XPOST https://api.paymentspring.com/api/v1/charge
 -d card_number=4111111111111111 -d card_exp_month=8 -d card_exp_year=2018
 -d amount=2000
```

> as the -u option in curl sets the HTTP basic auth credentials. Adding a colon after the username prevents curl from asking for a password.

To authenticate your calls to the PaymentSpring REST API, you’ll need to use an API key. PaymentSpring accounts have two sets of keys, test and live, each with a private key and a public key. The public key is a key that is used on web pages and forms for to create a token, and can be safely exposed to the public as it has no access to sensitive data. The private key is the key that you will use to authenticate with the API for all other calls. You should protect the private key and never expose it to anyone you do not want accessing all your data.


### Where can I get my API keys?

API keys can be found in the virtual terminal.

1. Log in to manage.paymentspring.com.
2. Click **Account** in the navigation menu on the left.
3. You’ll see your current API keys at the bottom of the page. We only allow these keys to show once for security reasons.
4. Click **Generate New Keys**. You can choose to expire the current keys now or in 1 hour.
5. You will see the new set of keys. Save them now, for they will be starred out the next time you visit this page.

Once you have activated your account, you will see the live set of keys as well as the test keys. Both can be used whenever you like; you do not need to leave the virtual terminal in live mode in order to make calls to the API using the live keys. Essentially, these keys are associated to accounts for two different merchants: a test merchant and a live merchant both associated to your PaymentSpring account.

<aside class="notice">
Have any feedback on this page? <a href="https://paymentspring.com/contact/">Let us know</a>!
</aside>
# Tokens

## Create a Token

> Sample Request:

```shell
curl -u public-api-key: https://api.paymentspring.com/api/v1/tokens
-d card_number="4111111111111111"
-d card_exp_month="1"
-d card_exp_year="2020"
-d csc="1234"
-d card_owner_name="John Doe"
```

> Expected Response Data:

```json
{
    "class": "token",
    "token_type": "credit_card",
    "id": "86c6a9466c",
    "card_type": "visa",
    "card_owner_name": "John Doe",
    "last_4": "1111",
    "card_exp_month": 1,
    "card_exp_year": 2020
}
```

###POST /tokens

Creates a token using a merchant’s public API key. This token can then be used to create a customer or to make a one-time charge. If the token is used for a one-time charge, it is then disabled so it can not be used again. A token can be created with either credit card information, or bank account information.

### Parameters

Parameter | Details
--------- | -----------
username | This request expects a merchant’s public API key to be provided as the username with a blank password. A private API key can not be used for this type of request.
token_type | Determines if this token contains credit card information, or bank account information. It can be set to credit_card or bank_account. If omitted, the token is treated as if it contains credit card information.
card_owner_name | Card owner name as it appears on card. This field is required if **token_type** is omitted or equals **credit_card**.
card_number | Full credit card number of a valid card. This field is required if **token_type** is omitted or equals **credit_card**.


## Retrieve a Token

> Sample Request:

```shell
curl -u private-api-key:
https://api.paymentspring.com/api/v1/tokens/62a987ed39
```

> Expected Response Data:

```json
{
    "class": "token",
    "token_type": "credit_card",
    "id": "86c6a9466c",
    "card_type": "visa",
    "card_owner_name": "John Doe",
    "last_4": "1111",
    "card_exp_month": 1,
    "card_exp_year": 2020
}
```

###GET /tokens

Gets basic detail for a saved token.

### Parameters

Parameter | Details
--------- | -----------
username | This request expects a merchant’s private API key to be provided as the username with a blank password. A public API key can not be used for this type of request.
token_id | ID of the token you want to fetch.
