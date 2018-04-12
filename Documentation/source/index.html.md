---
title: LunchBox - API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - javascript
  - ruby

toc_footers:
  - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introducción

Bienvenido a la API de LunchBox, puedes usar esta API para acceder a nuestros endpoints,
los cuales te pueden dar información sobre los restaurantes Universitarios y sus almuerzos.

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

# Restaurantes

## Todos los restaurantes

```javascript
// Usando axios

axios.get('api/restaurantes')
  .then(function (response) {
    console.log(response);
  })
  .catch(function (error) {
    console.log(error);
  });
```

```ruby
# Usando httparty
response = HTTParty.get('api/restaurantes')

puts response.body, response.code
```

> El código anterior retorna una lista JSON estructurada de la siguiente manera:

```json
[
  {
    "id": 1,
    "nombre": "Señor Gourmet",
    "imagenUrl": "http://lorempixel.com/400/200",
    "rangoPrecios": "Desde $8000 hasta $20000",
    "ubicacion": "Bloque 4"
  },
  {
    "id": 2,
    "nombre": "Donde Tavo",
    "imagenUrl": "http://lorempixel.com/400/200",
    "rangoPrecios": "Desde $5000 hasta $20000",
    "ubicacion": "Bloque 4"
  },
  {
    "id": 3,
    "nombre": "Mandarina",
    "imagenUrl": "http://lorempixel.com/400/200",
    "rangoPrecios": "Desde $8000 hasta $20000",
    "ubicacion": "Bloque 12"
  }
]
```

Este endpoint nos trae todos los restaurantes

### Petición HTTP

`GET http://lunchbox.com/api/restaurantes`

### Parámetros

No Aplica


## Detalle de un restaurante

```javascript
// Usando axios

axios.get('api/restaurantes/', {
    params: {
      idRestaurante: 1
    }
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
response = HTTParty.get('api/restaurantes?idRestaurante=1')

puts response.body, response.code
```

> El código anterior retorna un objeto JSON estructurado de la siguiente manera:

```json
{
  "id": 1,
  "nombre": "Señor Gourmet",
  "descripcion": "Disfruta de los mejores platos a un excelente precio",
  "coverImagen": "http://lorempixel.com/400/200",
  "horarioDeAtencion": "Lunes - Viernes de 6am a 6pm",
  "instrucciones": "Zona de comida de bloque 4"
}
```

Este endpoint devuelve un solo restaurante

### HTTP Request

`GET http://lunchbox.com/restaturante/<idRestaurante>`

### Parámetros

Parámetro | Descripción
--------- | -----------
idRestaurante | El id del restaurante que se desea buscar

# Almuerzos

## Menú del restaurante

```javascript
// Usando axios

axios.get('api/restaurantes/:idRestaurante/almuerzos')
  .then(function (response) {
    console.log(response);
  })
  .catch(function (error) {
    console.log(error);
  });
```

```ruby
# Usando httparty
response = HTTParty.get('api/restaurantes/:idRestaurante/almuerzos')

puts response.body, response.code
```

> El código anterior retorna una lista JSON estructurada de la siguiente manera:

```json
[
  {
    "id": 1,
    "nombre": "Bandeja Paisa",
    "descripcion": "Frijoles, Chicharrón, Carne Molida",
    "cantidad": "30",
    "precio": "8000"
  },
  {
    "id": 2,
    "nombre": "Lasagña",
    "descripcion": "La mejor Lasagña de la U",
    "cantidad": "11",
    "precio": "10000"
  },
]
```

Este endpoint nos trae los almuerzos que vende un restaurante específico

### Petición HTTP

`GET http://lunchbox.com/api/restaurantes/<idRestaurante>/almuerzos`

### Parámetros

Parámetro | Descripción
--------- | -----------
idRestaurante | El id del restaurante que se desea buscar

## Detalle de un almuerzo

```javascript
// Usando axios

axios.get('api/restaurantes/:idRestaurante/almuerzos/:idAlmuerzo')
  .then(function (response) {
    console.log(response);
  })
  .catch(function (error) {
    console.log(error);
  });
```

```ruby
# Usando httparty
response = HTTParty.get('api/restaurantes/:idRestaurante/almuerzos/:idAlmuerzo')

puts response.body, response.code
```

> El código anterior retorna un objeto JSON estructurado de la siguiente manera:

```json
{
  "id": 1,
  "nombre": "Bandeja Paisa",
  "descripcion": "Frijoles, Chicharrón, Carne Molida",
  "imagen": "http://lorempixel.com/400/200",
  "precio": "8000"
}
```

Este endpoint devuelve un solo almuerzo

### HTTP Request

`GET http://lunchbox.com/restaturante/<idRestaurante>/almuerzos/<idAlmuerzo>`

### Parámetros

Parámetro | Descripción
--------- | -----------
idRestaurante | El id del restaurante que se desea buscar
idAlmuerzo | El id del almuerzo que se desea buscar

# Órdenes

## Generar una orden

```javascript
// Usando axios

axios.post('/api/ordenes', {
    idAlmuerzo: '1',
    idCliente: '2',
    cantidad: '1'
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
response = HTTParty.post('/api/ordenes',
  query: {
    idAlmuerzo: '1',
    idCliente: '2',
    cantidad: '1'
  })

puts response.body, response.code
```

> El código anterior retorna el siguiente objeto JSON

```json
{
  "id": 1,
  "mensaje": "Almuerzo creado con exito",
  "subTotal": "8000"
}
```

Este endpoint crea una orden

### HTTP Request

`GET http://lunchbox.com/api/ordenes/`

### Parámetros

Parámetro | Descripción
--------- | -----------
idAlmuerzo | El id del almuerzo que se desea comprar
idCliente | El id del cliente que realiza la compra
cantidad | La cantidad de almuerzos que pide


## Consultar órdenes

```javascript
// Usando axios

axios.get('/api/:idUsuario/ordenes')
  .then(function (response) {
    console.log(response);
  })
  .catch(function (error) {
    console.log(error);
  });
```

```ruby
# Usando httparty
response = HTTParty.get('/api/:idUsuario/ordenes')

puts response.body, response.code
```

> El código anterior retorna la siguiente lista de objetos JSON

```json
[
  {
  "id": 1,
  "nombreAlmuerzo": "Bandeja Paisa",
  "nombreTienda": "Señor Gourmet",
  "estado": "En preparación",
  "total": "8000"
  }
]
```

Este endpoint retorna una lista de órdenes

### HTTP Request

`GET http://lunchbox.com/api/ordenes/<idCliente>`

### Parámetros

Parámetro | Descripción
--------- | -----------
idCliente | El id del cliente que realiza la compra
