# Endpoints

## HTTP response status codes

~~~
200 OK
Everything worked as expected

400 Bad request
The request didn’t work, often because a required parameter is missing or the content-type hasn’t been set e.g. an incorrect JSON request

401 Unauthorised
The request didn’t work because the combination of your API key and API token doesn't exist in our system or your integration has been disabled

409 Request failed
The parameters were valid but the request failed.

This can happen if you try to make a call but the sync status endpoint has timed out (after 3 minutes)

429 Too many requests
Too many requests hit the API too quickly. We recommend an exponential back-off of your requests

500, 502, 503, 504 Server error
Something went wrong on our end. You’ll have to try again later once we’ve fixed it
~~~

## 1. Products

### 1.1 Products create

~~~
POST /v1/products
~~~

#### Description
Use this endpoint to create new product.

#### Fields
* product_sku (int)
* sku_type (int)
* sku_listing (string)
* description (text)

#### Example payload

~~~json
{
  "product_sku": 145987,
  "sku_type": 258,
  "sku_listing": "pizza_category",
  "description":"Pepperoni pizza with cheese"
}
~~~

#### Example cURL request

~~~bash
curl -d "{ "product_sku": 145987, "sku_type": 258, "sku_listing": \
 "pizza_category", "description":"Pepperoni pizza with cheese" }" \
 -u <api_key>:<api_token> -X POST https://<api_url>/v1/products
~~~



### 1.2 Products view

~~~
GET /v1/products/{product_id}
~~~

#### Description
Use this endpoint to view product infomation.

#### Example cURL request

~~~bash
curl -u <api_key>:<api_token> -X GET https://<api_url>/v1/products/123456
~~~

### 1.3 Products update

~~~
PUT /v1/products/{product_id}
~~~

#### Description
Use this endpoint to update existing product.

#### Fields
* product_sku (int)
* sku_type (int)
* sku_listing (string)
* description (text)

#### Example payload

~~~json
{
  "product_sku": 145987,
  "sku_type": 258,
  "sku_listing": "pizza_category",
  "description":"Pepperoni pizza with cheese"
}
~~~

#### Example cURL request

~~~bash
curl -d "{ "product_sku": 145987, "sku_type": 258, "sku_listing": \
 "pizza_category", "description":"Pepperoni pizza with cheese" }" \
 -u <api_key>:<api_token> -X PUT https://<api_url>/v1/products
~~~

### 1.4 Products delete

~~~
DELETE /v1/products/{product_id}
~~~

#### Description
Use this endpoint to delete product.

#### Example cURL request

~~~bash
curl -u <api_key>:<api_token> -X DELETE https://<api_url>/v1/products/123456
~~~

## 2. Menu

### 2.1 Menu product create

~~~
POST /v1/menu
~~~

#### Description 
Add menu product to location with price

#### Fields
* location_id (int)
* product_sku (int)
* price (decimal)
* dose_type (int)

#### Example payload

~~~json
{
  "location_id": 14587,
  "product_sku": 123456,
  "price": "2.99",
  "dose_type": 1
}
~~~

#### Example cURL request

~~~bash
curl -d '{ "location_id": 14587, "product_sku": 123456, \
"price": "2.99", "dose_type": 1 }' \
 -u <api_key>:<api_token> -X PUT https://<api_url>/v1/products
~~~


### 2.2 Menu product view

~~~
GET /v1/menu/{menu_id}
~~~

#### Description
Use this endpoint to view menu product infomation.

#### Example cURL request

~~~bash
curl -u <api_key>:<api_token> -X GET https://<api_url>/v1/menu/123456
~~~

### 2.3 Menu product update

~~~
PUT /v1/menu/{menu_id}
~~~

#### Description
Use this endpoint to update existing menu product.

#### Fields
* location_id (int)
* product_sku (int)
* price (decimal)
* dose_type (int)

#### Example payload

~~~json
{
  "location_id": 14587,
  "product_sku": 123456,
  "price": "2.99",
  "dose_type": 1
}
~~~

#### Example cURL request

~~~bash
curl -d '{ "location_id": 14587, "product_sku": 123456, \
"price": "2.99", "dose_type": 1 }' \
 -u <api_key>:<api_token> -X PUT https://<api_url>/v1/menu/123456
~~~

### 2.4 Menu product delete

~~~
DELETE /v1/menu/{menu_id}
~~~

#### Description
Use this endpoint to delete menu product.

#### Example cURL request

~~~bash
curl -u <api_key>:<api_token> -X DELETE https://<api_url>/v1/menu/123456
~~~
