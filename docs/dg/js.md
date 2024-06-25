# Working with JavaScript

## Installation

To install the current release:

```
$ npm i statit_js
```

## Quick usage

To use the Statit REST API methods, first authenthicate yourself with your username and API token (see [Signing-in](https://help.gostatit.com/excel/signin/#authentication)):

```js
const { CoreAPI } = require('statit_js');

const statitAPI = new CoreAPI('<username>', '<api_key>');
```

`GET`, `LIST` and `DELETE` actions for collections and series are available in reference-by-ID format:

```js
let data = await statitAPI.getSerie('<serie_id>');
```

Alongside with the remaining `PUT` and all their respective `batch`  actions, they are also available in standard JSON request format:

```js
statitAPI.putSerieJSON({
    'id': '<serie_id>',
    ...
});
```

## Docs
