# Species Holdings API

Welcome to the Species360 API documentation for aggregated species
holdings from Zoological Information Management Software (ZIMS).

## Making a request

**Authentication**

To make any requests to the Species Holdings API you will need to
include an `Authorization` header with a valid API key in the format
`Bearer API_KEY`. You can obtain an API key by contacting Species360.

**Base Url**

To make a request to the Species Holdings API, you will need to use the
following base URL:

    https://api.species360.org/

**API endpoints**

<div class="informalexample">

**GET** ./v1/taxa/{taxonomy}/ex-situ-summary

| Parameter  | Description                                    |
|------------|------------------------------------------------|
| `taxonomy` | The taxonomy of the animal you are looking for |

**GET** ./v1/sis/{sisID}/ex-situ-summary

| Parameter | Description                                 |
|-----------|---------------------------------------------|
| `sisID`   | The sisId of the animal you are looking for |

JSON Response (for both endpoints):

| Path                           | Type     | Description                                                                          |
|--------------------------------|----------|--------------------------------------------------------------------------------------|
| `countries`                    | `Array`  | The countries that hold the species                                                  |
| `countries[].countryName`      | `String` | The name of the country                                                              |
| `countries[].countryISO`       | `String` | The ISO code of the country                                                          |
| `countries[].institutionCount` | `Number` | The number of institutions in the country that hold the species                      |
| `countries[].animalCount`      | `Number` | The number of animals in the country that hold the species                           |
| `population`                   | `Object` | The population of the species                                                        |
| `population.maleCount`         | `Number` | The number of males in the population                                                |
| `population.femaleCount`       | `Number` | The number of females in the population                                              |
| `population.otherCount`        | `Number` | Other includes unsexed, undeternmined, and any other type that is not male or female |
| `population.totalCount`        | `Number` | The total number of animals in the population                                        |
| `population.institutionCount`  | `Number` | The number of institutions that hold the species                                     |
| `studbooks`                    | `Array`  | Managed studbooks for the species                                                    |
| `studbooks[].organization`     | `String` | The organization that holds the studbook                                             |

Example Request:

    https://api.species360.org/v1/taxa/Echinotriton andersoni/ex-situ-summary

Example JSON Response:

``` json
{
  "countries" : [ {
    "countryName" : "United States",
    "countryISO" : "US",
    "countryLatitudeAverage" : 38.0,
    "countryLongitudeAverage" : -97.0,
    "institutionCount" : 3,
    "animalCount" : 43
  }, {
    "countryName" : "Japan",
    "countryISO" : "JP",
    "countryLatitudeAverage" : 36.0,
    "countryLongitudeAverage" : 138.0,
    "institutionCount" : 1,
    "animalCount" : 54
  } ],
  "population" : {
    "maleCount" : 1,
    "femaleCount" : 90,
    "otherCount" : 9,
    "totalCount" : 100,
    "institutionCount" : 5
  },
  "studbooks" : [ {
    "organization" : "Japanese Association of Zoos and Aquariums (JAZA)"
  } ]
}
```

Failed Request Response Example:

    {
    "status": 404,
    "message": "No taxonomy found for Echinotrit anderson"
    }

</div>
