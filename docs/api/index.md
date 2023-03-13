# Getting started with the REST API

This tutorial will take you the **main operations on the core Statit API**:

- [**Set-up and basic concepts**](#set-up-and-basic-concepts)

- [**Accessing time series**](#accessing-time-series)
    - Getting a single time serie
    - Getting a list of time series in a collection


## **Set-up and basic concepts**

### API format

The API accepts **HTTP GET and POST requests**.

All examples are presented with 'curl'. You can run requests with any client. 


### End-point

All requests must be addressed to: **https://api.gostatit.com/core**.

Core stands for the core API.

```bash
### request

curl https://api.gostatit.com/core

### response

{
  "message": "Welcome on Statit core API"
}

```

### Authentication

Your **requests must be identified with your credentials**: your username and API Key.

Your **username** and **API key** can be found in the **account section** in the home page for your profile.

The API uses **basic Http authentication**. On the command line, it looks like

```bash
### request

curl  -X POST \
      -u username:apikey \
      https://api.gostatit.com/core

### response

{
  "code": "ERROR_PARAM_REQUIRED", ...
}
```

### Actions

Once you are authentified, you can call specific actions: getSerie, getCollection, putSerie ...

You will do this by adding a json object to the query specifying the action called and the required inputs for the action.


```bash
### request

curl -X POST \
    -u username:apikey \
    -H "Content-Type: application/json" \
    -d '{"action": "getSerie", "input": {"id": "climat-fr/cei-m/region/bretagne/temp"}}' \
    https://api.gostatit.com/core

### response

{
  "Item": {
  "unit": "Degree Celcius",
  ...
  }
}

```

In the request above, we call the 'getSerie' action to get a single serie and pass a parameter called input with the 'id' of the serie we are requiring.

If you would like to learn the basics about serie identifiers, please head over to [Getting started on the web](/gs/index.md).


### Errors

If your request can not be processed, the API will return an error code with an error message.


```bash
### request

curl -X POST \
    -u username:apikey \
    -H "Content-Type: application/json" \
    -d '{"action": "getSerie" }' \
    https://api.gostatit.com/core

### response

{
  "code": "ERROR_PARAM_REQUIRED",
  "message": "Error. Your request is missing a required parameter. Please check the documentation"
}

```


## **Accessing time series**

### Getting a single time serie

We have already explored this in the example above.

#### Example

```bash
### request

curl -X POST \
    -u username:apikey \
    -H "Content-Type: application/json" \
    -d '{"action": "getSerie", "input": {"id": "clim/copernicus-r/daily/frh0/temp/real"}}' \
    https://api.gostatit.com/core

### response

{
  "Item": {
    "unit": "Degree Celcius",
    "frequency": "M",
    "sources": "Copernicus. Climate and Environmental Series",
    "name": "Monthly real temperature",
    "updated": "2021-03-10T17:14:45.504Z",
    "observations": "[[\"1979-01-01\", \"1.6\"], [\"1979-02-01\", \"5.3\"], [\"1979-03-01\", \"6.7\"], [\"1979-04-01\", \"8.5\"], [\"1979-05-01\", \"11.0\"], [\"1979-06-01\", \"14.6\"] ..."
    "description": "Average monthly temperature (degree Celcius)",
    "id": "clim/copernicus-r/daily/frh0/temp/real",
    "tags": []
  }
}
```


The Item object is quite explicit. It contains both serie metadata and data. Note that observations is a stringified array. You can transform it into an array using JSON parsers.


### Listing time series

The API let you request "children" series with a single parent.

As an example, if you are looking to get all indicators for waste in "Paris", you will call [dechets-fr/dma-dpt/paris/dechets-menagers-associes](https://gostatit.com/dechets/dma-dpt/paris/dechets-menagers-associes) and the request will return all related time series.

It is necessary to specify exactly the id of the parent. The size of the response is limited to 1MB.


#### Example

```bash
### request

curl -X POST \
    -u username:apikey \
    -H "Content-Type: application/json" \
    -d '{"action": "listSeries", "input": {"id": "dechets/dma-dpt/paris/dechets-menagers-associes"}}' \
    https://api.gostatit.com/core

### response

{
  "Items": [
    {
      "unit": "Tons",
      "frequency": "Y",
      "sources": "Base Sinoe de l'Ademe" ,
      "name": "Paris | Déchets ménagers et associés | Valorisation énergétique",
      "updated": "2021-02-24T07:05:32.120Z",
      "observations": "[[\"2009-01-01\", \"842125.33407\"], [\"2011-01-01\", \"833876.24514\"], [\"2013-01-01\", \"803965.81276\"], ...]",
      "description": "Paris. Déchets ménagers et associés. Valorisation énergétique",
      "id": "dechets-fr/dma-dpt/paris/dechets-menagers-associes/valo_energetique"
    },
    {...}
  ]
}

```


## **Pushing time series**

Before using the API to create a collection and push time series, we recommended you try doing it on the web first. Follow the [documentation](/gs/index.md) to understand the main concepts.

Once you have done this, we will only recap the main steps to:

- Create a collection
- Add series to the collection
- Add authorisations to the collection

### Creating a collection

You create a new collection by providing its 'id' and its 'name'. For this demo, we will create a temperature collection named 'temp'.

Replace username and apikey by your credentials below.


#### Example

```bash
### request

curl -X POST \
    -u username:apikey \
    -H "Content-Type: application/json" \
    -d '{"action": "putCollection", "input": {"id": "username/temp", "name": "My temperature collection" }}' \
    https://api.gostatit.com/core


### response

{
  "input": {
    "id": "username/temp"
  }
}
```

That's it. You have created your username/temp collection. Well done.


### Put a serie

Now, let's add a serie inside.

The required parameters for a serie are: id, name and frequency.


#### Example

```bash
### request

curl -X POST \
    -u username:apikey \
    -H "Content-Type: application/json" \
    -d '{"action": "putSerie", "input": {"id": "username/temp/new-york", "name": "New York temperatures", "frequency": "D", "observations": "[[\"2021-03-07\", 10.0], [\"2021-03-08\", 11.4]]" }}' \
    https://api.gostatit.com/core



### response

{
  "input": {
    "id": "username/temp/new-york"
  }
}
```

That's it. You have added the username/temp/new-york serie to your collection. Congrats.


### Add an authorisation

Now is the time to create an authorisation to make your serie available to other people.

To keep it simple, we will make our serie public. To achieve this, we will use "public" as a username.

Before we do this, try to access your series on https://gostatit.com/YOUR-USERNAME/temp/new-york. If you are not signed-in, you will not be able to see the serie.

Then, create the authorisation.


#### Example

```bash
### request

curl -X POST \
    -u username:apikey \
    -H "Content-Type: application/json" \
    -d '{"action": "putCollectionAuth", "input": { "id": "username/temp", "username": "public", "type": "viewer" }}' \
    https://api.gostatit.com/core


### response

{
  "input": {
    "id": "username/temp",
    "username": "public",
    "type": "viewer"
  }
}
```

Well done. Now check https://gostatit.com/YOUR-USERNAME/temp/new-york. Your collection and serie can be accessed by everyone.

### Removing the authorisation

Time to clean-up. Let's remove the "publics" authorisation.

#### Example

```bash
### request

curl -X POST \
    -u username:apikey \
    -H "Content-Type: application/json" \
    -d '{"action": "deleteCollectionAuth", "input": { "id": "username/temp", "username": "public" }}' \
    https://api.gostatit.com/core


### response

{
  "input": {
    "id": "username/temp",
    "username": "public",
  }
}
```

### Removing the serie

Now, let's remove the serie from the collection.


```bash
### request

curl -X POST \
    -u username:apikey \
    -H "Content-Type: application/json" \
    -d '{"action": "deleteSerie", "input": { "id": "username/temp/new-york" }}' \
    https://api.gostatit.com/core


### response

{
  "input": {
    "id": "username/temp/new-york",
  }
}
```

### Removing the collection

Now that we have emptied the collection, we can safely remove it.


```bash
### request

curl -X POST \
    -u username:apikey \
    -H "Content-Type: application/json" \
    -d '{"action": "deleteCollection", "input": { "id": "username/temp" }}' \
    https://api.gostatit.com/core


### response

{
  "input": {
    "id": "username/temp",
  }
}
```

That's it. You have completed the tutorial. Congratulations.

### Next steps

You will find the full API reference [here](reference.md)
