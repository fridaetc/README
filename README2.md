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
Functions that returns promises (reject, resolve) for specified api calls
`AgilityComponents.Api`

#### apiCall
Function to use with other api calls in order to be able to cancel the call at any point
1. Create new instance: `let apiCall = AgilityComponents.Api.apiCall()`
2. Create new token to use in api call: `let token = apiCall.token`
3. Cancel an ongoing call: `apiCall.cancel()`

#### get
Function to GET data from an endpoint
`get(string, object={}, token=null)`
string: The endpoint where to get data
object: Params to add to the endpoint
token: Token created by apiCall to be able to cancel the call

Example for `GET /getData?param1=x&param2=y&param2=z`:
```
AgilityComponents.Api.get('getData', {param1: "x", param2: ["y", "z"]}, token).then(response => {
  //response = response data
}).catch(e => {
  //e.type = type of error
  //e.message = error message
});
```

#### post
`AgilityComponents.Api.post`

#### put
`AgilityComponents.Api.put`

#### _delete
`AgilityComponents.Api._delete`



### Charts

#### Bar

#### Pie

#### Column (future)
Not ready to use
#### Map (future)
Not ready to use
