# Reference REST API

This API reference covers Statit core API functions:

- putCollection
- updateCollection
- getCollection
- deleteCollection

- putCollectionAuth
- deleteCollectionAuth

- putSerie
- batchPuSerie
- getSerie
- listSeries
- deleteSerie

API version: 1.0.1


## Errors

Requests with errors return a response object with the following attributes:
- code: Error code
- message: Error message



## putCollection

putCollection is the action used to create a new collection. putCollection can not be used to overwrite an existing collection. Collection updates need to be performed with updateCollection.

#### Parameters

- action: putCollection
- input:
  - id - String - Required: ID of the collection. Authorised characters: alphanumerical and ".", "-", "_"
  - name - String - Required: Name of the collection
  - about - String - Optional: A field describing the collection in one sentence. Text format
  - frequency - String - Optional: A descriptive field. Authorised values: D, W, M, Q, S, Y
  - description  - String - Optional: A descriptive field. Text or markdown format.
  - start - String - Optional: A descriptive field for the start date of the series (YYYY-MM-DD)
  - end -  string - Optional: A descriptive field for the end date of the series (YYYY-MM-DD)
  - language - String - Optional: A descriptive field for the language used in the collection. Authorised values: en, fr, de
  - tags - Array - Optional: Tags related to the collection

#### Response

- input - Object:
  - id: id the collection




## updateCollection

updateCollection is used to update the fields of an existing collection

#### Parameters

- action: updateCollection
- input:
  - id - String - Required: ID of the collection. Needs to be the id an existing collection.
  - name - String - Optional: Name of the collection
  - about - String - Optional: A field describing the collection in one sentence. Text format
  - frequency - String - Optional: A descriptive field. Authorised values: D, W, M, Q, S, Y
  - description  - String - Optional: A descriptive field. Text or markdown format.
  - start - String - Optional: A descriptive field for the start date of the series (YYYY-MM-DD)
  - end -  string - Optional: A descriptive field for the end date of the series (YYYY-MM-DD)
  - language - String - Optional: A descriptive field for the language used in the collection. Authorised values: en, fr, de
  - tags - Array - Optional: Tags related to the collection

#### Response

- input - Object:
  - id: id the collection





## getCollection

getCollection is used to get a collection

#### Parameters

- action: getCollection
- input:
  - id - Required - String: ID of the collection requested

#### Response

- Item - Object:
  - id - String: ID of the collection.
  - name - String: Name of the collection
  - about - String: A field describing the collection in one sentence. Text format
  - frequency - String: A descriptive field. Authorised values: D, W, M, Q, S, Y
  - description  - String: A descriptive field. Text or markdown format.
  - start - String: A descriptive field for the start date of the series (YYYY-MM-DD)
  - end -  string: A descriptive field for the end date of the series (YYYY-MM-DD)
  - language - String: A descriptive field for the language used in the collection. Authorised values: en, fr, de
  - tags - Array: Tags related to the collection




## deleteCollection

deleteCollection is used to delete a collection. Only collections free of series and with no authorisations can be deleted.

#### Parameters

- action: deleteCollection
- input:
  - id - Required - String: ID of the collection requested

#### Response

- input - Object:
  - id: id the collection





## putCollectionAuth

putCollectionAuth is used to grant an authorisation to access a collection

#### Parameters

- action: putCollectionAuth
- input:
  - id - String - Required: ID of the collection
  - username - String - Required: The username for the person being granted the authorisation
  - type - String - Required: The type of authorisation. Authorised values: viewer, member, editor, administrator

- Viewers can access the collection and series
- Members can access the collection and series and comment
- Editors can access the collection and series and edit them
- Editors can access the collection and series, edit them and manage access

#### Response

- input - Object:
  - id: id the collection
  - username: username
  - type: type of access granted




## deleteCollectionAuth

deleteCollectionAuth is used to delete an authorisation for a specific user

#### Parameters

- action: deleteCollectionAuth
- input:
  - id - Required - String: ID of the collection requested
  - username - Required - String: username of the user

#### Response

- input - Object:
  - id: id the collection
  - username: username of the user




## putSerie

putSerie is used to put a serie inside a collection

#### Parameters

- action: putSerie
- input - Object:
  - id - String - Required: ID of the serie. Authorised characters: alphanumerical and ".", "-", "_" and "/"
  - name - String - Required: Name of the serie
  - frequency - String - Required: Frequency of the serie. Authorised values: D, W, M, Q, S, Y
  - description - String - Optional: Description of the serie. Text format
  - unit - String - Optional: Unit of the serie
  - sources - Array - Optional: List of sources
  - tags - Array - Optional: List of tags for the serie
  - notes - Array - Optional: List of notes
  - observations - String - Optional: a stringified array of individual observations "[[date1, val1], [date2, val2]]"

#### Response

- input - Object:
  - id: id the serie





## batchPutSerie

batchPutSerie is used to put multiple series inside a collection.

Up to 25 series can be put in a single call.

#### Parameters

- action: batchPutSerie
- input - Array:
  - serie object as in putSerie

#### Response

- input - Array:
  - ids of the series pushed





## getSerie

getSerie is used to get a single time serie from a collection

#### Parameters

- action: getSerie
- input:
  - id - Required - String: ID of the serie requested

#### Response

- Item - Object:
  - id - String - Required: ID of the serie. Authorised characters: alphanumerical and ".", "-", "_" and "/"
  - name - String - Required: Name of the serie
  - frequency - String - Required: Frequency of the serie. Authorised values: D, W, M, Q, S, Y
  - description - String - Optional: Description of the serie. Text format
  - observations - String - Optional: a stringified array of individual observations "[[date1, val1], [date2, val2]]"
  - unit - String - Optional: Unit of the serie
  - sources - Array - Optional: List of sources
  - tags - Array - Optional: List of tags for the serie
  - notes - Array - Optional: List of notes




## listSeries

listSeries is used to get all children series under a single parent ID.

As an example, an/example is the parent ID of an/example/serie1 and an/example/serie1

#### Parameters

- action: 'istSeries
- input:
  - id - Required - String: ID of the parentID

#### Response

- Items - Array of Item (see get serie)





## deleteSerie

deleteSerie is used to delete a serie.

#### Parameters

- action: deleteSerie
- input:
  - id - Required - String: ID of the serie

#### Response

- input - Object:
  - id: id the serie
