# Species Holdings API

Welcome to the Species360 API documentation. This API provides access to
the species holdings data in ZIMS from Species360

## Making a request

<div class="informalexample">

**Authentication**

Before making any requests to the Species Holdings API, you will need to
authenticate and recive a bearer token to attach to your request. To get
a token, you will need to include the following information in the
request: Audience, Grant_type, AccessToken Url, Clint id, and Client
Secret

</div>

<div class="informalexample">

To make a request to the Species Holdings API, you will need to use the
following base URL:

    https://api.species360.org/

**API endpoints**

<div class="informalexample">

**GET** Unresolved directive in api-guide.adoc -
include::{snippets}/Species Holdings Summary/path-parameters.adoc\[\]

JSON Response: Unresolved directive in api-guide.adoc -
include::{snippets}/Species Holdings Summary/response-fields.adoc\[\]

Example Request:

    https://api.species360.org/v1/taxa/Echinotriton andersoni/ex-situ-summary

Example JSON Resposne: Unresolved directive in api-guide.adoc -
include::{snippets}/Species Holdings Summary/response-body.adoc\[\]

</div>

</div>
