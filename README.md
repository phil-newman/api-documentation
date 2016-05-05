# Musement API Documentation

Current latest version 3.0.0

Here you can find documentation to help you start integrating with Musement. Explore our events catalog step by step and easily set up the checkout flow into your app or website.

The Musement API gives you a set of endpoints to GET all the information about our products such as locations, opening hours, availability, prices, discounts and more. Also your application can create and manage carts, tickets and orders and make payments.

Clicking on the links below you can find all step by step instructions that you need

1. [API for Authentication]({{ baseUrl }}/authentication.md)
2. [API for Catalog]({{ baseUrl }}/catalog.html)
3. [API for Booking]({{ baseUrl }}/booking.html)
4. [API for Search]({{ baseUrl }}/search.hmtl)

### Swagger sandbox tool

[https://api.musement.com/documentation](https://api.musement.com/documentation)

### Endpoints

* *Production*: https://api.musement.com/api/v3
* *QA-testing*: https://api-qa.musement.com/api/v3

## Generic info

### Language 

Musement content is available in different languages. You can specify the language using the standard header `Accept-Language` If the content is not available for the language requested the English version is returned

##### _Example_

Request information for a specific city in spanish.

```
GET /api/v3/cities/2
Accept-Language: es
```

```
{
  "id": 2,
  "top": true,
  "has_concierge": true,
  "name": "Roma",
  "code": "rome",
  "content": "El más grande y asombroso museo al aire libre del mundo. Esta es Roma, la capital de Italia, primera gran metrópoli da la humanidad y una de las ciudades más amplias de Europa. Roma concentra sus tres milenios de historia en los testimonios arquitectónicos y artísticos que te dejan sin aliento, obras maestras que la convierten en una de las ciudades más visitadas y admiradas en el mundo. Hay quien dice que una vida no es suficiente para descubrir todos sus tesoros, y sin embargo, basta un sólo día para dejarse seducir por el encanto decadente y embriagador de la antigua capital de una de las civilizaciones antiguas más importantes, el Imperio Romano.Roma es la ciudad con la más alta concentración de bienes históricos y arquitectónicos del mundo.",
  "latitude": 41.898,
  "longitude": 12.483,
  "country": {
    "id": 82,
    "name": "Italia",
    "iso_code": "IT"
  },
  "cover_image_url": "https://static1.musement.com/cover/0001/03/rome_event-2986.jpeg?event",
  "url": "https://www.musement.com/es/roma/"
}
```

### Currency

To change the currency of the prices you must use `X-Musement-Currency`

##### Availables currencies

| Code          | Name               |
| ------------- |:------------------:|
| EUR           | Euro (default)     |
| USD           | USA dollar         |
| GBP           | Pound sterling     |
| AED           | Dirham             |
| SEK           | Swedish krone      |
| DKK           | Danish krone       |
| AUD           | Australian dollar  |
| CAD           | Canadian dollar    |

##### _Example_

Getting prices in Swedish Krone

```
GET /api/v3/events/1/dates/2016-02-10
X-Musement-Currency: SEK
```

```
...
  "retail_price": {
    "currency": "SEK",
    "value": 380,
    "formatted_value": "SEK 380.00"
  }
```

and is USA dollars

```
GET /api/v3/events/1/dates/2016-02-10
X-Musement-Currency: USD
```

```
...
  "retail_price": {
    "currency": "USD",
    "value": 37,
    "formatted_value": "$ 37.00"
  }
```

### API Versioning

The corrent latest verision is: `3.0.0`

When you start a new project that uses _Musement API_ set `X-Musement-Version` to the current latest version. This assure that the model in the response will be stable with time. If you don't set the header the server will alwayas returns the latest version. 

When a new version is released you can check the documentation and choose to upgrade your header or remain with your version. You can also specify different version for different calls. But we discourage this practice.

##### _Example_

```
GET /api/v3/events/1/dates/2016-02-10
X-Musement-Version: 3.0.0
```
