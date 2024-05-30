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

    https://api.species360.org/data/

**API endpoints**

**GET** ./v1/taxa/{taxonomy}/ex-situ-summary

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th style="text-align: left;">Parameter</th>
<th style="text-align: left;">Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="text-align: left;"><p><code>taxonomy</code></p></td>
<td style="text-align: left;"><p>The taxonomy of the animal you are
looking for</p></td>
</tr>
</tbody>
</table>

JSON Response:

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th style="text-align: left;">Path</th>
<th style="text-align: left;">Type</th>
<th style="text-align: left;">Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="text-align: left;"><p><code>countries</code></p></td>
<td style="text-align: left;"><p><code>Array</code></p></td>
<td style="text-align: left;"><p>The countries that hold the
species</p></td>
</tr>
<tr class="even">
<td
style="text-align: left;"><p><code>countries[].countryName</code></p></td>
<td style="text-align: left;"><p><code>String</code></p></td>
<td style="text-align: left;"><p>The name of the country</p></td>
</tr>
<tr class="odd">
<td
style="text-align: left;"><p><code>countries[].countryISO</code></p></td>
<td style="text-align: left;"><p><code>String</code></p></td>
<td style="text-align: left;"><p>The ISO code of the country</p></td>
</tr>
<tr class="even">
<td
style="text-align: left;"><p><code>countries[].institutionCount</code></p></td>
<td style="text-align: left;"><p><code>Number</code></p></td>
<td style="text-align: left;"><p>The number of institutions in the
country that hold the species</p></td>
</tr>
<tr class="odd">
<td
style="text-align: left;"><p><code>countries[].animalCount</code></p></td>
<td style="text-align: left;"><p><code>Number</code></p></td>
<td style="text-align: left;"><p>The number of animals in the country
that hold the species</p></td>
</tr>
<tr class="even">
<td style="text-align: left;"><p><code>population</code></p></td>
<td style="text-align: left;"><p><code>Object</code></p></td>
<td style="text-align: left;"><p>The population of the species</p></td>
</tr>
<tr class="odd">
<td
style="text-align: left;"><p><code>population.maleCount</code></p></td>
<td style="text-align: left;"><p><code>Number</code></p></td>
<td style="text-align: left;"><p>The number of males in the
population</p></td>
</tr>
<tr class="even">
<td
style="text-align: left;"><p><code>population.femaleCount</code></p></td>
<td style="text-align: left;"><p><code>Number</code></p></td>
<td style="text-align: left;"><p>The number of females in the
population</p></td>
</tr>
<tr class="odd">
<td
style="text-align: left;"><p><code>population.otherCount</code></p></td>
<td style="text-align: left;"><p><code>Number</code></p></td>
<td style="text-align: left;"><p>Other includes unsexed, undeternmined,
and any other type that is not male or female</p></td>
</tr>
<tr class="even">
<td
style="text-align: left;"><p><code>population.totalCount</code></p></td>
<td style="text-align: left;"><p><code>Number</code></p></td>
<td style="text-align: left;"><p>The total number of animals in the
population</p></td>
</tr>
<tr class="odd">
<td
style="text-align: left;"><p><code>population.institutionCount</code></p></td>
<td style="text-align: left;"><p><code>Number</code></p></td>
<td style="text-align: left;"><p>The number of institutions that hold
the species</p></td>
</tr>
<tr class="even">
<td style="text-align: left;"><p><code>studbooks</code></p></td>
<td style="text-align: left;"><p><code>Array</code></p></td>
<td style="text-align: left;"><p>Managed studbooks for the
species</p></td>
</tr>
<tr class="odd">
<td
style="text-align: left;"><p><code>studbooks[].organization</code></p></td>
<td style="text-align: left;"><p><code>String</code></p></td>
<td style="text-align: left;"><p>The organization that holds the
studbook</p></td>
</tr>
</tbody>
</table>

Example Request:

    https://api.species360.org/data/v1/taxa/Echinotriton andersoni/ex-situ-summary

Example JSON Response:

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

Failed Request Response Example:

    {
    "status": 404,
    "message": "No taxonomy found for Echinotrit anderson"
    }
