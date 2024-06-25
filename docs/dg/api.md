# The APIs

Statit provides two API endpoints at `https://api.gostatit.com`: 

- `/core`: all the actions (account, series, collections, charts...) one can do on Statit
- `/functions`: utilities used by the spreadsheet plugins (single values for example)

API requests and responses are in JSON format. Requests to either endpoint take the following form:

```json
{
    "action": "YOUR_API_ACTION",
    "input": {
        ...
    }
}
```

Statit returns data in case of success or otherwise an error, in which case the following atrributes are set:

- `code`: An explicit error code
- `message` (optional): An explicit error message

#### Example

***Request***
```json
{
    "action": "getObs",
     "input": {
        "id": "xr/daily/eur/usd" 
    }
}
```

***Response***
```json
{
  "value": 1.073
}
```

## Authenthication

## Core API reference


### putSerie

**putSerie** is used to **put a serie inside a collection**

putSerie is used to publish a new serie. Every call to putSerie will replace the previously saved serie.

**Parameters**

- **action**: putSerie
- **input** - **Object**:
    - **id** - **String** - *required*. ID of the serie. Accepted characters: alphanumerical (A to z, 0 to 9) and ".", "-", "_" and "/"
    - **name** - **String** - *required*. Name of the serie
    - **frequency** - **String** - *required*. Frequency of the serie. Accepted values: D, W, M, Q, S, Y
    - **description** - **String** - *optional*. Description of the serie. Text format
    - **unit**- **String** - *optional*. Unit of the serie
    - **sources** - **String** - *optional*. Sources
    - **notes** - **String** - *optional*. Publication notes
    - **observations** - **String** - *optional*. An array of individual observations, for instance ["2021-03-07", 62.0], ["2021-03-08", 105.0]

**Response**

- **input** - **Object**:
    - **id**: id of the serie




### batchPutSerie

**batchPutSerie** is used to put multiple series inside a collection.

Up to 25 series can be put in a single call.

**Parameters**

- **action**: batchPutSerie
- **input** - **Array**:
    - Serie object as in putSerie

**Response**

- **input** - Array:
    - **ids** of the series pushed



### listSeries



listSeries is used to get all children series under a single parent ID.

As an example, a/b/c is the parent ID of a/b/c/serie1 and a/b/c/serie2

**Parameters**

- **action**: listSeries
- **input** - **Object**:
    - **id** - *required* - **String**. ID of the parentID

**Response**

- **Items** - Array of Item (see get serie)



### updateSerie

**updateSerie** is used to **update a serie**

**Parameters**

- **action**: updateSerie
- **input** - **Object**:
    - **id** - **String** - *required*. ID of the serie. Accepted characters: alphanumerical (A to z, 0 to 9) and ".", "-", "_" and "/"
    - **name** - **String** - *optional*. Name of the serie
    - **frequency** - **String** - *optional. Frequency of the serie. Accepted values: D, W, M, Q, S, Y
    - **description** - **String** - *optional*. Description of the serie. Text format
    - **unit**- **String** - *optional*. Unit of the serie
    - **sources** - **String** - *optional*. Sources
    - **notes** - **String** - *optional*. Publication notes
    - **observations** - **String** - *optional*. An array of individual observations, for instance ["2021-03-07", 62.0], ["2021-03-08", 105.0]


**Response**

- **input** - **Object**:
    - **id**: id of the serie



### deleteSerie

deleteSerie is used to remove a serie.

**Parameters**

- **action**: deleteSerie
- **input** - **Object**:
    - **id** - *required* - **String**. ID of the serie

**Response**

- **input** - **Object**:
    - **id**: id of the serie

### updateCollection

**updateCollection** is used to **update the properties of an existing collection**

**Parameters**

- **action**: updateCollection
- **input** - **Object**:
    - **id** - **String** - *required*. ID of the collection. Needs to be the id an existing collection.
    - **name** - **String** - *optional*. Name of the collection
    - **description** - **String** - *optional*. A descriptive field. Text or markdown format.
    - **tags** - **Array** - *optional*. Tags related to the collection

**Response**

- **input** - **Object**:
    - **id**: id the collection

## Functions API reference





