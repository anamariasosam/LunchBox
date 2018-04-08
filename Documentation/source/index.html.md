---
title: LunchBox - API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - ruby
  - javascript

toc_footers:
  - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introducción

Bienvenido a la API de LunchBox, puedes usar esta API para acceder a nuestros endpoints,
los cuales te pueden dar información sobre los restaurantes Universitarios y sus almuerzos que se encuentran en nuestra base de datos.

Puedes encontrar en el area negra el código y puedes cambiar según el lenguaje de programación que estés utilizando.



<!-- # Authentication

> To authorize, use this code:

```ruby
require 'lunchbox'

api = LunchBox::APIClient.authorize!('123456789')
```

```python
import lunchbox

api = lunchbox.authorize('123456789')
```

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "Authorization: 123456789"
```

```javascript
const lunchbox = require('lunchbox');

let api = lunchbox.authorize('123456789');
```

> Make sure to replace `123456789` with your API key.

LunchBox uses API keys to allow access to the API. You can register a new LunchBox API key at our [developer portal](http://lunchbox.com/developers).

LunchBox expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: 123456789`

<aside class="notice">
You must replace <code>123456789</code> with your personal API key.
</aside> -->

# Almuerzos

## Mostar todos los almuerzos

```ruby
require 'lunchbox'

api = LunchBox::APIClient.authorize!('123456789')
api.dishes.get
```

```shell
curl "http://lunchbox.com/api/dishes"
  -H "Authorization: 123456789"
```

```javascript
const lunchbox = require('lunchbox');

let api = lunchbox.authorize('123456789');
let dishes = api.dishes.get();
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "name": "Bandeja Paisa",
    "breed": "calico",
    "fluffiness": 6,
    "cuteness": 7
  },
  {
    "id": 2,
    "name": "Max",
    "breed": "unknown",
    "fluffiness": 5,
    "cuteness": 10
  }
]
```

This endpoint retrieves all dishes.

### HTTP Request

`GET http://lunchbox.com/api/dishes`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include dishes that have already been adopted.



## Mostrar un almuerzo específico

```ruby
require 'lunchbox'

api = LunchBox::APIClient.authorize!('123456789')
api.dishes.get(2)
```

```shell
curl "http://lunchbox.com/api/dishes/2"
  -H "Authorization: 123456789"
```

```javascript
const lunchbox = require('lunchbox');

let api = lunchbox.authorize('123456789');
let max = api.dishes.get(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Max",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a specific kitten.

### HTTP Request

`GET http://lunchbox.com/dishes/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to retrieve

## Eliminar un almuerzo específico

```ruby
require 'lunchbox'

api = LunchBox::APIClient.authorize!('123456789')
api.dishes.delete(2)
```

```shell
curl "http://lunchbox.com/api/dishes/2"
  -X DELETE
  -H "Authorization: 123456789"
```

```javascript
const lunchbox = require('lunchbox');

let api = lunchbox.authorize('123456789');
let max = api.dishes.delete(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ":("
}
```

This endpoint deletes a specific kitten.

### HTTP Request

`DELETE http://lunchbox.com/dishes/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete
