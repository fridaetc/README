- Components
  - Api
    - apiCall
    - get
    - post
    - put
    - _delete
  - Charts
    - Bar
    - Pie
    - Column
    - Map
  
## Components
`import AgilityComponents from 'agility-components';`

### Api
Functions that returns promises (reject, resolve) for specified api calls.
- Resolve will send back the data
- Reject will send back an error with a type and a message
`AgilityComponents.Api`

#### apiCall
Function to use with other api calls in order to be able to cancel the call at any point
1. Create new instance: `let apiCall = AgilityComponents.Api.apiCall()`
2. Create new token to use in api call: `let token = apiCall.token`
3. Cancel an ongoing call: `apiCall.cancel()`

#### get
Function to GET data from an endpoint
`get(string, object={}, token=null)`
- string: The endpoint where to get data
- object: Params to add to the endpoint
- token: Token created by apiCall to be able to cancel the get

Example for `GET /getData?param1=x&param2=y&param2=z`:
```
AgilityComponents.Api.get('getData', {param1: "x", param2: ["y", "z"]}, token).then(response => {
}).catch(error => {
});
```

#### post
Function to POST data to an endpoint
`post(string, object={}, token=null)`
- string: The endpoint where to post data
- object: Body to send with the post
- token: Token created by apiCall to be able to cancel the post

Example for `POST /postData BODY {param1: "x}`:
```
AgilityComponents.Api.post('postData', {param1: "x"}, token).then(response => {
}).catch(error => {
});
```

#### put
Function to PUT data to an endpoint
`put(string, object={}, token=null)`
- string: The endpoint where to put data
- object: Body to send with the put
- token: Token created by apiCall to be able to cancel the post

Example for `PUT /putData BODY {param1: "x}`:
```
AgilityComponents.Api.put('putData', {param1: "x"}, token).then(response => {
}).catch(error => {
});
```

#### _delete
Function to DELETE data for an endpoint
`_delete(string, token=null)`
- string: The endpoint where to delete data
- token: Token created by apiCall to be able to cancel the post

Example for `DELETE /deleteData`:
```
AgilityComponents.Api._delete('deleteData', token).then(response => {
}).catch(error => {
});
```

### Charts

#### Bar

#### Pie

#### Column (future)
Not ready to use
#### Map (future)
Not ready to use
