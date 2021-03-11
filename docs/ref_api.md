# Reference REST API

This API reference covers Statit core API functions:

- putCollection
- putCollectionAuth
- updateCollection
- deleteCollection
- getSerie
- listSeries
- deleteSerie

API version: 2021-02-12



### getSerie

getSerie is used to get a single serie from a collection.

#### Parameters

- action: getSerie
- input:
  - id - required - string: ID of the serie requested

#### Response

- Item:
  - id - string - required: ID of the serie. Authorised characters: alphanumerical and ".", "-", "_" and "/"
  - name - string - required: Name of the serie
  - frequency - string - required: Frequency of the serie. Authorised values: D, W, M, Q, S, Y
  - description - string - optional: Description of the serie. Text format
  - observations - string - optional: a stringified array of individual observations "[[date1, val1], [date2, val2]]"
  - unit - string - optional: Unit of the serie
  - sources - array - optional: List of sources
  - tags - array - optional: List of tags for the serie
  - notes - array - optional: List of notes

#### Errors

- code: An error code
- message: An error message




### Listing time series in a collection

#### Introduction

It is possible to get multiple series in a single go.

For the moment, the API accepts requests that specify the parent and will provide all the "children" series.

As an example, if we are looking to get all waste indicators for "déchets ménagers associés" in the "Paris" department, we will query [dechets-fr/dma-dpt/paris/dechets-menagers-associes](https://gostatit.com/dechets-fr/dma-dpt/paris/dechets-menagers-associes).

It is necessary to specify exactly the id of the parent. The response returned will have a maximum size of 1MB.





#### Parameters

- action: 'listSeries'
- input: { id: 'id' of the parent }

#### Response:

There are three different responses:

- If you are not authorised to access this collection, you will receive an error.
- If you are authorised to access the collection and children series exist, you will receive a JSON response with an Items object containing all the series.
- If are authorised to access the collection but the serie does not exist, you will receive an empty object

The items in the Items array are the same as the Item in getSerie




### Creating a collection

You create a new collection by providing its 'id' and its 'name'.


#### Example:

```bash
### request

curl -X POST \
    -u username:apikey \
    -H "Content-Type: application/json" \
    -d '{"action": "putCollection", "input": \
      {"id": "[USERNAME]/[COLLECTION_KEY]", \
      "name": [COLLECTION_NAME]}}' \
    https://api.gostatit.com/core

### response

{
  "input": {
    "id": "[USERNAME]/[COLLECTION_KEY]"
  }
}
```


#### Parameters

- action: putCollection
- input:
  - id - string - required: ID of the collection
  - name - string - required: Name of the collection
  - about - string - optional: A descriptive field. Text format
  - frequency - string - optional: A descriptive field. Authorised values: D, W, M, Q, S, Y
  - description  - string - optional: A descriptive field. Text or markdown format.
  - start - string - optional: A descriptive field for the start date of the series (YYYY-MM-DD)
  - end -  string - optional: A descriptive field for the end date of the series (YYYY-MM-DD)
  - language - string - optional: A descriptive field for the language used in the collection. Authorised values: en, fr, de
  - tags - array - optional: Tags related to the collection


#### Response

There are two different responses:

- If your username is incorrect or if the 'id' or 'name' fail validation, you will receive an error.
- If the request is successful, you will receive an input object with the 'id' of the collection


### Put a serie

Now that you have created the collection, you can push series inside.

The required parameters for a serie are: serie ID, name and frequency. The serie ID is built based on the username, the collection key and a specific serie id.

Slashes are authorised inside serie keys.


#### Example:

```bash
### request

curl -X POST \
    -u username:apikey \
    -H "Content-Type: application/json" \
    -d '{"action": "putSerie", "input": { "id": "USERNAME/COLLECTION_KEY/SERIE_KEY", "name": "SERIE_NAME", "frequency": "D" }}' \
    https://api.gostatit.com/core


### response

{
  "input": {
    "id": "USERNAME/COLLECTION_KEY/SERIE_KEY"
  }
}
```


#### Parameters

- action: putSerie
- input:
  - id - string - required: ID of the serie
  - name - string - required: Name of the serie
  - frequency - string - required: Frequency of the serie. Authorised values: D, W, M, Q, S, Y
  - description - string - optional: Description of the serie. Text format
  - unit - string - optional: Unit of the serie
  - sources - array - optional: List of sources
  - tags - array - optional: List of tags for the serie
  - notes - array - optional: List of notes
  - observations - string - optional: a stringified array of individual observations "[[date1, val1], [date2, val2]]"


#### Response

There are two different responses:

- If the username, the collection key, the serie key or the serie parameters are invalid, you will receive an error.
- If the request is successful, you will receive an input object with the 'id' of the serie


### Add an authorisation

You have created a collection and pushed a serie inside.

Now is the time to create an authorisation to make your serie available to other people.

For simplicity, we will make the serie public.


#### Example:

```bash
### request

curl -X POST \
    -u username:apikey \
    -H "Content-Type: application/json" \
    -d '{"action": "putSerie", "input": { "id": "USERNAME/COLLECTION_KEY/SERIE_KEY", "name": "SERIE_NAME", "frequency": "D" }}' \
    https://api.gostatit.com/core


### response

{
  "input": {
    "id": "USERNAME/COLLECTION_KEY/SERIE_KEY"
  }
}
```


#### Parameters

- action: putSerie
- input:
  - id - string - required: ID of the serie
  - name - string - required: Name of the serie
  - frequency - string - required: Frequency of the serie. Authorised values: D, W, M, Q, S, Y
  - description - string - optional: Description of the serie. Text format
  - unit - string - optional: Unit of the serie
  - sources - array - optional: List of sources
  - tags - array - optional: List of tags for the serie
  - notes - array - optional: List of notes
  - observations - string - optional: a stringified array of individual observations "[[date1, val1], [date2, val2]]"


#### Response

There are two different responses:

- If the username, the collection key, the serie key or the serie parameters are invalid, you will receive an error.
- If the request is successful, you will receive an input object with the 'id' of the serie
