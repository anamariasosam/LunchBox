# Validaciones

```javascript
// Usando axios

axios.post('https://lunchbox-api.herokuapp.com/v1/customers/:customer_id/orders',  {
    quantity: '2'
  })
  .then(function (response) {
    console.log(response);
  })
  .catch(function (error) {
    console.log(error);
  });
```
> El código anterior retorna una objeto JSON estructurado de la siguiente manera:

```json
{
	"error": {
		"menu_item": [
			"must exist"
		],
		"menu_item_id": [
			"can't be blank"
		]
	}
}
```

Cuando se crea un recurso y los parámetros no están o son incorrectos a los esperados se obtendrá un json con lo que información faltante y un código http  422

Código | Significado
---------- | -------
422 | La solicitud está bien formada pero fue imposible seguirla debido a errores semánticos.
