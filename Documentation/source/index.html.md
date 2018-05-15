---
title: LunchBox - API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - javascript
  - ruby
toc_footers:
  - <a href='https://www.getpostman.com/run-collection/d32f2e7c0122d53df721' target="_blank">Run in postman</a>
  - <a href='https://docs.google.com/document/d/1ZRJyUz3MCTYHDI2E-2EF4KJLtsich9JNV11fEqozBvw/edit?usp=sharing' target="_blank">Estudio Legal</a>
  - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

includes:
  - errors
  - validaciones

search: true
---

# Introducción

Bienvenido a la API de LunchBox, puedes usar esta API para acceder a nuestros endpoints,
los cuales te pueden dar información sobre los restaurantes Universitarios y sus almuerzos.

[![Run in Postman](https://run.pstmn.io/button.svg)](https://app.getpostman.com/run-collection/d32f2e7c0122d53df721)

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

LunchBox uses API keys to allow access to the API. You can register a new LunchBox API key at our [developer portal](http://lunchbox-api.herokuapp.com/developers).

LunchBox expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: 123456789`

<aside class="notice">
You must replace <code>123456789</code> with your personal API key.
</aside> -->

# Restaurantes

## Todos los restaurantes

```javascript
// Usando axios

axios.get('https://lunchbox-api.herokuapp.com/v1/restaurants')
  .then(function (response) {
    console.log(response);
  })
  .catch(function (error) {
    console.log(error);
  });
```

```ruby
# Usando httparty
response = HTTParty.get('https://lunchbox-api.herokuapp.com/v1/restaurants')

puts response.body, response.code
```

> El código anterior retorna una lista JSON estructurada de la siguiente manera:

```json
[
	{
		"data": {
			"id": "2",
			"type": "restaurant",
			"attributes": {
				"name": "Donde Tavo",
				"image_url": "https://source.unsplash.com/400x200/?restaurant",
				"location": "Bloque 4",
				"min_price": 5000,
				"max_price": 20000
			}
		}
	},
	{
		"data": {
			"id": "3",
			"type": "restaurant",
			"attributes": {
				"name": "Mandarina",
				"image_url": "https://source.unsplash.com/400x200/?restaurant",
				"location": "Bloque 12",
				"min_price": 8000,
				"max_price": 20000
			}
		}
	},
	{
		"data": {
			"id": "1",
			"type": "restaurant",
			"attributes": {
				"name": "Señor Gourmet",
				"image_url": "https://source.unsplash.com/400x200/?restaurant",
				"location": "Bloque 4",
				"min_price": 8000,
				"max_price": 20000
			}
		}
	}
]
```

Este endpoint nos trae todos los restaurantes

### Petición HTTP

`GET http://lunchbox-api.herokuapp.com/v1/restaurants`

### Parámetros

No Aplica


## Detalle de un restaurante

```javascript
// Usando axios

axios.get('https://lunchbox-api.herokuapp.com/v1/restaurants/:restaurant_id')
  .then(function (response) {
    console.log(response);
  })
  .catch(function (error) {
    console.log(error);
  });
```

```ruby
# Usando httparty
response = HTTParty.get('https://lunchbox-api.herokuapp.com/v1/restaurants/:restaurant_id')

puts response.body, response.code
```

> El código anterior retorna un objeto JSON estructurado de la siguiente manera:

```json
{
	"data": {
		"id": "1",
		"type": "restaurant",
		"attributes": {
			"name": "Señor Gourmet",
			"image_url": "https://source.unsplash.com/400x200/?restaurant",
			"location": "Bloque 4",
			"min_price": 8000,
			"max_price": 20000
		}
	}
}
```

Este endpoint devuelve el detalle de un solo restaurante

### HTTP Request

`GET http://lunchbox-api.herokuapp.com/restaturante/:restaurant_id`

### Parámetros

Parámetro | Descripción
--------- | -----------
restaurant_id | El id del restaurante que se desea buscar

# Almuerzos

## Menú del restaurante

```javascript
// Usando axios

axios.get('https://lunchbox-api.herokuapp.com/v1/restaurants/:restaurant_id/menu_items')
  .then(function (response) {
    console.log(response);
  })
  .catch(function (error) {
    console.log(error);
  });
```

```ruby
# Usando httparty
response = HTTParty.get('https://lunchbox-api.herokuapp.com/v1/restaurants/:restaurant_id/menu_items')

puts response.body, response.code
```

> El código anterior retorna una lista JSON estructurada de la siguiente manera:

```json
[
	{
		"data": {
			"id": "1",
			"type": "menu_item",
			"attributes": {
				"item_name": "Papas Mexicanas",
				"description": "Pico de gallo, guacamole, sour cream",
				"price": "13500.0",
				"image_url": "https://source.unsplash.com/400x200/",
				"quantity": 98,
				"restaurant_id": 1,
				"restaurant_name": "Señor Gourmet"
			}
		}
	}
]
```

Este endpoint nos trae los almuerzos que vende un restaurante específico

### Petición HTTP

`GET http://lunchbox-api.herokuapp.com/v1/restaurants/:restaurant_id/menu_items`

### Parámetros

Parámetro | Descripción
--------- | -----------
restaurant_id | El id del restaurante que se desea buscar

## Detalle de un almuerzo

```javascript
// Usando axios

axios.get('https://lunchbox-api.herokuapp.com/v1/restaurants/:restaurant_id/menu_items/:menu_item_id')
  .then(function (response) {
    console.log(response);
  })
  .catch(function (error) {
    console.log(error);
  });
```

```ruby
# Usando httparty
response = HTTParty.get('https://lunchbox-api.herokuapp.com/v1/restaurants/:restaurant_id/menu_items/:menu_item_id')

puts response.body, response.code
```

> El código anterior retorna un objeto JSON estructurado de la siguiente manera:

```json
{
	"data": {
		"id": "1",
		"type": "menu_item",
		"attributes": {
			"item_name": "Papas Mexicanas",
			"description": "Pico de gallo, guacamole, sour cream",
			"price": "13500.0",
			"image_url": "https://source.unsplash.com/400x200/",
			"quantity": 98,
			"restaurant_id": 1,
			"restaurant_name": "Señor Gourmet"
		}
	}
}
```

Este endpoint devuelve un solo almuerzo

### HTTP Request

`GET https://lunchbox-api.herokuapp.com/v1/restaurants/:restaurant_id/menu_items/:menu_item_id`

### Parámetros

Parámetro | Descripción
--------- | -----------
restaurant_id | El id del restaurante que se desea buscar
menu_item_id | El id del almuerzo que se desea buscar

# Órdenes

## Generar una orden

```javascript
// Usando axios

axios.post('https://lunchbox-api.herokuapp.com/v1/customers/:customer_id/orders', {
    menu_item_id: '1',
    quantity: '2'
  })
  .then(function (response) {
    console.log(response);
  })
  .catch(function (error) {
    console.log(error);
  });
```

```ruby
# Usando httparty
response = HTTParty.post('https://lunchbox-api.herokuapp.com/v1/customers/:customer_id/orders',
  query: {
    menu_item_id: '1',
    quantity: '2'
  })

puts response.body, response.code
```

> El código anterior retorna el siguiente objeto JSON

```json
{
	"data": {
		"id": "3",
		"type": "order",
		"attributes": {
			"menu_item_id": 1,
			"customer_id": 2,
			"quantity": 2,
			"order_status_id": 1,
			"restaurant_id": 1,
			"total": "27000.0",
			"menu_item_name": "Papas Mexicanas",
			"customer_name": "Juan Pablo Montoya",
			"restaurant_name": "Señor Gourmet",
			"order_status_description": "Recibida"
		}
	}
}
```

Este endpoint crea una orden

### HTTP Request

`GET https://lunchbox-api.herokuapp.com/v1/customers/:customer_id/orders`

### Parámetros

Parámetro | Descripción
--------- | -----------
customer_id | El id del cliente que realiza la compra
menu_item_id | El id del almuerzo que se desea comprar
quantity | La cantidad de almuerzos que pide


## Consultar órdenes

```javascript
// Usando axios

axios.get('https://lunchbox-api.herokuapp.com/v1/customers/:customer_id/orders')
  .then(function (response) {
    console.log(response);
  })
  .catch(function (error) {
    console.log(error);
  });
```

```ruby
# Usando httparty
response = HTTParty.get('https://lunchbox-api.herokuapp.com/v1/customers/:customer_id/orders')

puts response.body, response.code
```

> El código anterior retorna la siguiente lista de objetos JSON

```json
[
	{
		"data": {
			"id": "3",
			"type": "order",
			"attributes": {
				"menu_item_id": 1,
				"customer_id": 2,
				"quantity": 2,
				"order_status_id": 1,
				"restaurant_id": 1,
				"total": "27000.0",
				"menu_item_name": "Papas Mexicanas",
				"customer_name": "Juan Pablo Montoya",
				"restaurant_name": "Señor Gourmet",
				"order_status_description": "Recibida"
			}
		}
	}
]
```

Este endpoint retorna una lista de órdenes

### HTTP Request Comprador

`GET https://lunchbox-api.herokuapp.com/v1/customers/:customer_id/orders`

### Parámetros

Parámetro | Descripción
--------- | -----------
customer_id | El id del cliente que realiza la compra


### HTTP Request Restaurante
`GET https://lunchbox-api.herokuapp.com/v1/restaurants/:restaurant_id/orders`

### Parámetros

Parámetro | Descripción
--------- | -----------
restaurant_id | El id del restaurante al que se le realizó la compra
