# @dreipol/vue-fetch-route

## API

<!-- Generated by documentation.js. Update this documentation by updating the source code. -->

### connect

Wire up a vuex store with the app

**Parameters**

-   `store` **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)** A vuex store containing the `router` module

Returns **[Function](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/function)** Unsync function

### decorateRecords

Route config creation helper

**Parameters**

-   `records` **[Array](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Array)** A route record array describing a list of available routes (optional, default `[]`)
-   `parents` **[Array](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Array)** The records' parental hierarchy, the first item being the oldest (optional, default `[]`)

Returns **[Array](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Array)** The enhanced route records, ready for being used by `vue-router`

### decorateRecord

Create a route descriptor ready for consumation by `vue-router`

**Parameters**

-   `record` **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)** The base config object received from the server
    -   `record.name` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** The page's name
    -   `record.path` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** The base path prior to any manipulation by params or query
    -   `record.component` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** The component name used by the route
    -   `record.children` **[Array](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Array)** A list of child route definitions
    -   `record.alias` **([string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String) \| [Array](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Array)&lt;[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)>)** A list of child route definitions
    -   `record.redirect` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** A list of child route definitions
    -   `record.meta` **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)** An object of properties that shall be available later on in the route (optional, default `{}`)
    -   `record.api` **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)** The api definition containing all necessary info to fetch and store this route's data (optional, default `{}`)
        -   `record.api.fetch` **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)** The fetch definition used to create the api endpoint
        -   `record.api.fetched` **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)** A data object, containing prefetched data from the server
    -   `record.parents`  

Returns **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)** A newly created route record

### compareRecords

Compare two route definitions, ignoring irrelevant information such as hash

**Parameters**

-   `to` **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)** A route record describing the previous location
-   `from` **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)** A route record describing the next location

Returns **[boolean](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Boolean)** A flag indicating if two records are identical

### invokeFetch

Start a fetch request

**Parameters**

-   `route` **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)** A route descriptor object
    -   `route.params` **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)** All currently active params
    -   `route.query` **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)** The currently active query object
    -   `route.meta`  

Returns **[Promise](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Promise)** A promise returning route data of a page

### namespaced

Access namespaced module in vuex store

Returns **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** The namespaced module name

### compileFetchUrl

Compile full fetch api endpoint by using params and query objects

**Parameters**

-   `fetchUrl` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** A base string, used as a template
-   `params` **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)** A params object that fills the params gap in the `fetchUrl` template string
-   `query` **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)** A query object that is being appended to the `fetchUrl` template string

Returns **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** The fully compiled fetch url

### setEndpoint

Register an api url and create a function through which api data can be accessed (via cache or api call)

**Parameters**

-   `fetch` **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)** A fetch endpoint definition
    -   `fetch.url` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** The basic url prior to any manipulation
    -   `fetch.params` **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)** A list of base params that are being merged with specific params, later on
    -   `fetch.query` **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)** A query object that is being merged with the specific query object, later on
    -   `fetch.cache`   (optional, default `true`)

Returns **[Function](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/function)** Return a handler function for accessing fetch data via a returned promise

### createUrlKeys

Create endpoint urls for fetching and storing

**Parameters**

-   `compileFn` **[Function](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/function)** The method to compile a fetch/storage url out of a raw url
-   `fetchUrl` **[string](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** The raw url
-   `params` **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)** The params object
-   `query` **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)** The query object

Returns **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)** An object containing the fetch and the storage url

### filterQueryParams

Filter query params for djangoCMS static placeholders

**Parameters**

-   `query` **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)** The input query object (optional, default `{}`)
-   `store` **Vuex.Store** The vuex store object

Returns **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)** The filtered query object

### removeQueryParams

Remove query params for djangoCMS static placeholders

**Parameters**

-   `query` **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)** The query object (optional, default `{}`)

Returns **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)** The stripped query object
