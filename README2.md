This package contains reusable components that constitute the building blocks of the `agility-app` package. These can be instantiated separately for further customisation. 

Here's an overview of the exposed components.

- Components
  - api
    - apiCall
    - get
    - post
    - put
    - _delete
  - Widgets
    - Bar
    - Pie
    - Column
    - Map
    - Empty
    - Table
  - Filters
    - Checkbox
    - DateRangePicker
    - Dropdown
    - NumberRange
    - Slider
  - styles
    - colors
  
## Components

Installing from NPM.

`npm install --save agility-components`

Importing:

`import AgilityComponents from 'agility-components';`

### Api
Functions that returns promises (reject, resolve) for specified api calls.
- Resolve will send back the data
- Reject will send back an error with a type and a message

`import { Api } from 'agility-components';`

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
Api.get('getData', {param1: "x", param2: ["y", "z"]}, token).then(response => {
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
Api.post('postData', {param1: "x"}, token).then(response => {
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
Api.put('putData', {param1: "x"}, token).then(response => {
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
Api._delete('deleteData', token).then(response => {
}).catch(error => {
});
```

### Widgets
`import { Widgets } from 'agility-components';`

#### Bar
`Widgets.Bar`

|    Prop    |     Type     |            Description            |
|------------|--------------|-----------------------------------|
|  `config`  | object | Highcharts configuration object https://api.highcharts.com/highcharts/ |
|  `preview`  | boolean |  If the widget is shown in the workspace or as a preview in the widgets list  |

Example `config`:
```
{
  yAxis: {
    title: {
      text: 'Cows'
    }
  },
  series: [{
    name: 'Cows',
     data: [
      {name: "Brown cow", y: 45},
      {name: "Red cow", y: 1},
    ],
    color: 'black'
  }]
}
```

#### Pie
`Widgets.Pie`

|    Prop    |     Type     |            Description            |
|------------|--------------|-----------------------------------|
|  `config`  | object | Highcharts configuration object https://api.highcharts.com/highcharts/  |

Example `config`:
```
{
  yAxis: {
    title: {
      text: 'Cows'
    }
  },
  series: [{
    name: 'Cows',
    data: [
      {name: "Brown cow", y: 45},
      {name: "Red cow", y: 1},
    ]
  }],
  colors: ["brown", "red"]
}
```

#### Column
`Widgets.Column`

|    Prop    |     Type     |            Description            |
|------------|--------------|-----------------------------------|
|  `config`  | object | Highcharts configuration object https://api.highcharts.com/highcharts/  |

Example `config`:
```
{
  yAxis: {
    title: {
      text: 'Number of Cows'
    }
  },
  xAxis: {
    title: {
      text: 'Type of Cow'
    },
    categories: ["Normal cow", "Angry cow"]
  },
  series: [
    {
      name: 'Brown',
      color: 'brown',
      data: [43, 0]
    },
    {
      name: 'Red',
      color: 'red',
      data: [2, 1]
    }
  ]
}
```

#### Map
`Widgets.Map`
Not ready to use yet


#### Empty
`Widgets.Empty`

Gray box with a message "Use the panel on the left to add filters to this widget"


#### Table
`Widgets.Table`

|    Prop    |     Type     |            Description            |
|------------|--------------|-----------------------------------|
|  `config`  | object | Table configuration |
|  `data`  | object{hits: int, data: array[{}]} |  Table data |

Example `config`:
```
{
  rowsPerPage: 8,
  sort: "asc",
  sortBy: "cowtype",
  columns: [
    {name: "Cow Name", key: "cowname"},
    {name: "Cow Colour", key: "cowcolor"},
    {name: "Cow Type", key: "cowtype"}
  ]
}
```
Example `data`:
```
{
  hits: 46,
  data: [
    {cowname: "Rosa", cowcolor: "Red", cowtype: "Angry Cow"},
    {cowname: "Mona Lisa", cowcolor: "Brown", cowtype: "Normal Cow"},
    + 6 more...
  ]
}
```

### Filters
`import { Filters } from 'agility-components';`

#### Checkbox
`Filters.Checkbox`

Props: https://react.semantic-ui.com/modules/checkbox

#### DateRangePicker
`Filters.DateRangePicker`

Props: https://github.com/airbnb/react-dates (DateRangePicker)

#### Dropdown
`Filters.Dropdown`

Props: https://react.semantic-ui.com/modules/dropdown

#### NumberRange
`Filters.NumberRange`

|    Prop    |     Type     |            Description            |
|------------|--------------|-----------------------------------|
|  `min`  | int | Min range value |
|  `max`  | int |  Max range value |
|  `warning`  | string |  Warning message below filter |
|  `onChange`  | function |  On values change callback function |

#### Slider
`Filters.Slider`

|    Prop    |     Type     |            Description            |
|------------|--------------|-----------------------------------|
|  `min`  | int | Min range value |
|  `max`  | int |  Max range value |
|  `label`  | string |  Label centered under slider in between input fields |
|  `values`  | array[start, end]|  Selected range, for example [3, 5]  |
|  `marks`  | object |  Marked out values, for example {0: "Start", 10: "End"} |
|  `onChange`  | function |  On values change callback function |

### Styles
`import { styles } from 'agility-components';`

#### Colors
`styles.colors`

Object of predefined colours
