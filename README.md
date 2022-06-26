# Simple Books API #
[![Netlify Status](https://api.netlify.com/api/v1/badges/e73ed186-e18e-48ed-ad8c-729b16ea9907/deploy-status)](https://app.netlify.com/sites/glitchmemahmud/deploys)
This API allows to reserve a book.

The API is available at `https://simple-books-api.glitch.me`

## [Click here to see the report](https://glitchmemahmud.netlify.app/)

## Endpoints ##

### Message ###

GET `/`

Returns the Message of the API.

### Status ###

GET `/status`

Returns the status of the API.

### books Lists###

GET `/books`

Returns a list of books.
###Filter books List###

GET `/books?type=non-fiction`

Returns a list of books based on types.

Optional query parameters:

- type: fiction or non-fiction

### Details of a single book ###

GET `books/id`

Retrieve detailed information about a book.


## API Authentication ##

To submit or view an order, you need to register your API client.

POST `/api-clients/`

The request body needs to be in JSON format and include the following properties:

 - `clientName` - String
 - `clientEmail` - String

 Example

 ```
{
   "clientName": "Reza",
   "clientEmail": "rezoanul@example.com"
}
 ```

The response body will contain the access token. The access token is valid for 7 days.

**Possible errors**

Status code 409 means conflict - "API client already registered." Try changing the values for `clientEmail` and `clientName` to something else.


### Submit an order ###

POST `/orders`

Allows you to submit a new order. Requires authentication.

The request body needs to be in JSON format and include the following properties:

 - `bookId` - Integer - Required
 - `customerName` - String - Required

Example
```
POST /orders/
Authorization: Bearer <YOUR TOKEN>

{
  "bookId": 1,
  "customerName": "Rakib"
}
```

The response body will contain the order Id.

### Get all orders ###

GET `/orders`

Allows you to view all orders. Requires authentication.

### Get an order ###

GET `/orders/orderId`

Allows you to view an existing order. Requires authentication.

### Update an order ###

PATCH `/orders/orderId`

Update an existing order. Requires authentication.

The request body needs to be in JSON format and allows you to update the following properties:

 - `customerName` - String

 Example
```
PATCH /orders/PF6MflPDcuhWobZcgmJy5
Authorization: Bearer <YOUR TOKEN>

{
  "customerName": "Rakibul Islam"
}
```

### Delete an order ###

DELETE `/orders/orderId`

Delete an existing order. Requires authentication.

The request body needs to be empty.

 Example
```
DELETE /orders/PF6MflPDcuhWobZcgmJy5
Authorization: Bearer <YOUR TOKEN>
```
