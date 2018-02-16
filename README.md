- App
  - Config
     - Categories
     - Widgets
     - Filters
     - Options
     - Results
  - Icons
  - Colors
  - Components

## App
`import AgilityApp from 'agility-app';`

## Config

Configuration objects
```
config = {{
   categories,
   widgets,
   filters,
   options,
   results
}}
```

### Categories
```
categories = {
   uniqueCategoryKey: {
      key,
      ...
   },
   ...
}
```

|    Key    | Required   |     Type     |            Description            |
|-----------|-----------|--------------|-----------------------------------|
|  `name`   |  Yes  | string       |   Category title                  |
|  `color`  | |  string(`color`)       |   Category colour, from list of predefined colours or hex like #000000                 |
|  `icon`   |        | string(`icon`)       |   Category icon, from list of predefined icons                   |
|  `label`  |      | boolean      |   Defines if the category label should be visible in the bottom left corner of the widgets|


### Widgets
```
widgets = {
   uniqueWidgetKey: {
      key,
      ...
   },
   ...
}
```

|    Key    | Required  |     Type     |            Description            |
|-----------|-----------|--------------|-----------------------------------|
|  `category` | Yes | string(`uniqueCategoryKey`) | Sets the widgets category which appears in widget list and label of the widget |
|  `name`   | Yes |   string       |   Widgets default title (can be renamed by user)  |
|  `container`   |  Yes     | object       |   Data handling config  |
|  `container.component`   | Yes | string/function(`WidgetContainerComponent`)     |   Which component should handle the data. Write a custom one or choose from predefined ones: DataContainer, ...  |
|  `container.endpoint`  | If container.component = string | string  |  The endpoint to fetch the data from. Ignored if container.component is a custom component   |
|  `presentation`   |  If container.component = string  | object       |  Visual presentation config   |
|  `presentation.component` | If container.component = string | string/function(`WidgetPresentationComponent`)  |  Which component should present the data. Write a custom one or choose from predefined ones: BarChart, PieChart, Table ... Ignored if container.component is a custom component  |
|  `presentation.chartType`  | | string |  Used when presentation.component is predefined. Defines what type of chart to show in the homepage thumbnails. Choose from predefined ones: bar, pie, column, map   |
|  `presentation.chartTitle`  | | string    |  Used when presentation.component is predefined and a chart. Set the y title and tooltip title of the chart  |
|  `presentation.chartColors`  | | array[string(`color`)]   |  Used when presentation.component is predefined. Sets the widget content color (if applicable)  |
|  `entitlement`   | Yes | string  |  Determines if the user can see the widgets content / add it to a workspace  |
|  `exportEntitlement` | | string  |  Determines if the user can export the widgets data  |
|  `sidebar`   |   |object       |  What will be shown in the widget tab in the sidebar   |
|  `sidebar.filters`   | | boolean  |  Determines if to show filter section in sidebar, which displays filters defined in the filter config. If not defined or false and container.component is predefined, data will be presented straight away in the widget rather than clicking "run" from sidebar   |
|  `sidebar.options`|  | array[string(`uniqueOptionKey`)]  |  Shows options section in sidebar populated with content from options config   |
|  `minW`   |    | int       |  The smallest width the widget can shrink to   |
|  `minH`   |  | int       |  The smallest height the widget can shrink to   |
|  `w`   |     | int       |  The initial width for the widget   |
|  `h`   |    | int       |  The initial height for the widget   |


### Filters
Creates filters for widgets
```
filters = {
   key,
   ...
   filters: {
      uniqueFilterKey: {
         key,
         ...
      }
   }
}
```
Filters:

|    Key    | Required |     Type     |            Description            |
|-----------|----------|--------------|-----------------------------------|
|  `endpoints`  | Yes | object | Endpoints |
|  `endpoints.filterValues`  | If filters = defined | string | Endpoint to populate all the filter components with values |
|  `endpoints.totalResults`  | if totalResults = defined | string | Endpoint to get the stats at the top of the sidebar |
|  `totalResults`  | | array[object{key, name}] | What to display in the stats, key comes from the endpoints response data |



Filters.filters:

|    Key    | Required |     Type     |            Description            |
|-----------|----------|--------------|-----------------------------------|
|  `name`  | Yes | string | Title of the filter |
|  `category`  | Yes | string(`uniqueCategoryKey`) | Sets the filters category which appears in filters list |
|  `component` | Yes | string/function(`FilterComponent`)| Which component should present the filter. Write a custom one or choose from predefined: Dropdown, Checkbox, NumberRange, SliderRange ...  |
|  `autoComplete`  | | boolean | If filter should have autocomplete, only works when component is Dropdown |
|  `autoCompleteEndpoint`  | If autoComplete = true | string | Endpoint to populate the dropdown filter with autocomplete results |
|  `wildcard`  | | boolean | If filter is autocomplete and Dropdown, option to add wildcard search from the search string  |



### Options
Creates widget settings
```
options = {
   uniqueOptionKey: {
      key,
      ...
   },
   ...
}
```

|    Key    | Required |     Type     |            Description            |
|-----------|----------|--------------|-----------------------------------|
|  `name`  | Yes | string | Title of the option  |
|  `component`  | Yes | string/function(`OptionComponent`) | Which component should present the option. Write a custom one or choose from predefined: Dropdown, Checkbox, NumberRange, SliderRange ...  |
|  `defaultValue` | |string | Default selected value of the option |
|  `singleSelect` | If defaultValue = defined |string | Sets the option to single select |
|  `items` | If component = string | array[{text, value}] | Items for the option |
|  `disabled` | | function | If the option should be disabled based on other options values. Gets param selectedOptions, should return true/false |


### Results
Settings for the results
```
results = {
   key,
   ...
}
```

|    Key    |     Required    |     Type    |            Description           |
|-----------|-----------------|--------------|-----------------------------------|
|  `name`  | | string | Title of the results |
|  `description`  | | string | Description of the results |
|  `entitlement`  | Yes | string | Determines if the user can see the results |
|  `exportEntitlement`  | | string | Determines if the user can export the result data |
|  `container`   |  Yes     | object       |   Data handling config  |
|  `container.component`   | Yes | string/function(`ResultsContainerComponent`)     |   Which component should handle the data. Write a custom one or choose from predefined ones: ResultsContainer, ...  |
|  `container.endpoint`  | If container.component = string | string  |  The endpoint to fetch the data from. Ignored if container.component is a custom component   |
|  `presentation`   |  If container.component = string  | object       |  Visual presentation config   |
|  `presentation.component` | If container.component = string | string/function(`ResultsresentationComponent`)  |  Which component should present the data. Write a custom one or choose from predefined ones: Table ... Ignored if container.component is a custom component  |
|  `presentation.rowLink`  | | function | If presentation.component = Table, defines what url each row in the table should have. Gets param data, should return string |
|  `presentation.rowLinkEntitlement`  | If presentation.rowLink = defined | string | If presentation.component = Table, determines if the user can open the row link |
|  `presentation.rowsPerPage`  | | int | If presentation.component = Table, defines rows per page, defaults to 8. Min 1 |
|  `presentation.sort`  | | string | If presentation.component = Table, defines what to sort after, asc or desc  |
|  `presentation.sortBy`  | | string | If presentation.component = Table, defines what column to sort after  |
|  `presentation.columns`  | If presentation.component = Table | array[{name, key, w}] | If presentation.component = Table, defines which fields to show in the results. w = width of the table cell based on a 16 grid |


## Icons
https://material.io/icons/ 

Agility specific:
activity, air temp, businesses, cattle, chart area, chart bar, chart column, chart delta, chart line, chart pivot, chart scatter, companies, contracts, crop, droplets, equipment, farms, fields, fields vert, flower, fog, fuel, holdings, humidity, mass, precipitation, products, soil temp, stock, trade, trade items, treatments, volume, wind speed 


## Colors
|    Name    |     Color     |   HEX   |
|------------|---------------|---------|
|  `slime`  |  ![#B5CC18](https://placehold.it/15/B5CC18/000000?text=+)   | #B5CC18 |
|  `orange`  |  ![#F2711C](https://placehold.it/15/F2711C/000000?text=+)   | #F2711C |
|  `yellow`  |  ![#FBBD08](https://placehold.it/15/FBBD08/000000?text=+)   | #FBBD08 |
|  `green`  |  ![#84BF42](https://placehold.it/15/84BF42/000000?text=+)   | #84BF42 |
|  `teal`  |  ![#00B5AD](https://placehold.it/15/00B5AD/000000?text=+)   | #00B5AD |
|  `red`  |  ![#DB2828](https://placehold.it/15/DB2828/000000?text=+)   | #DB2828 |
|  `blue`  |  ![#2185D0](https://placehold.it/15/2185D0/000000?text=+)   | #2185D0 |
|  `violet`  |  ![#6435C9](https://placehold.it/15/6435C9/000000?text=+)   | #6435C9 |
|  `purple`  |  ![#A333C8](https://placehold.it/15/A333C8/000000?text=+)   | #A333C8 |
|  `pink`  |  ![#E03997](https://placehold.it/15/E03997/000000?text=+)   | #E03997 |
|  `brown`  |  ![#A5673F](https://placehold.it/15/A5673F/000000?text=+)   | #A5673F |
|  `grey`  |  ![#767676](https://placehold.it/15/767676/000000?text=+)   | #767676 |
|  `black`  |  ![#1B1C1D](https://placehold.it/15/1B1C1D/000000?text=+)   | #1B1C1D |
|  `white`  |  ![#FFFFFF](https://placehold.it/15/FFFFFF/000000?text=+)   | #FFFFFF |
|  `unknown`  |  ![#AAAAAA](https://placehold.it/15/AAAAAA/000000?text=+)   | #AAAAAA |


## Components
Custom components have access to props via this.props.x

`WidgetContainerComponent`
`WidgetContainerPresentation`
`FilterComponent`
`OptionComponent`
`ResultsContainerComponent`
`ResultsContainerPresentation`


### `WidgetContainerComponent`
Data props
   - catConfig = `uniqueCategoryKey` object
   - collapsed = If the workspace is collapsed or not
   - config = `uniqueWidgetKey` object
   - id = Id of the widget 
   - messages = App error, info, success and warning messages
   - query = Widgets active query
   - widget = Settings and info about the widget
   - workspaceId = Id of the current workspace 
   
Functions props
   - setErrorMessage = Function to call to set or remove an error message for the widget, setErrorMessage("Something went wrong"/false)
   - setHasData = Function to call to set if the widget has got data or not, if false an info message will be shown automatically, setHasData(true/false)
   - setInfoMessage = Function to call to set or remove an info message for the widget, setInfoMessage({title: "Info title", text: "Info text"}/false)
   - setInfoPopup = Function to call to set the table data and warnings for the widgets top right popup, setInfoPopup(["Warning message 1", "Warning message 2"], [{title: "Column 1 title", value: "Column 1 value"}])
   - setIsLoading = Function to call to show or hide the loader for the widget, setIsLoading(true/false)


### `WidgetContainerPresentation`
Data props
   - data = The repsonse data from the endpoint call
   - preview = If the widget is shown in the workspace or as a preview in the widgets list
   - catConfig = `uniqueCategoryKey` object
   - config = `uniqueWidgetKey` object

### `FilterComponent`
Data props
   - config = `uniqueFilterKey` object
   - id = Active widget id
   - items = Filter items
   - selected = Selected filter items
   - messages = App error, info, success and warning messages
   
Functions props
   - onChange = Function to call when the selected value for the filter changed, will be sent back en the selected prop, onChange("New value")
   - onError = Function to call to set or remove an error message for the filter, onError("Something went wrong"/false)

### `OptionComponent`
Data props
   - id = Active widget id
   - type = `uniqueOptionKey`
   - config = `uniqueOptionKey` object
   - selected = Selected option items
   - messages = App error, info, success and warning messages
   - items = `uniqueOptionKey` object items
   - disabled = If option should be disabled or not
   - singleSelect = If option should be single select or not
   
Functions props
   - onChange = Function to call when the selected value for the option changed, will be sent back en the selected prop, onChange("New value")

### `ResultsContainerComponent`
Data props
   - id = Id of the current active widget 
   - workspaceId = Id of the current workspace 
   - config = `results` object
   - messages = App error, info, success and warning messages
   - entitlements = Current user entitlement codes
   - widget = Settings and info about the current active widget
   - query = Current active widget active query
   
Functions props
   - setErrorMessage = Function to call to set or remove an error message for the results, setErrorMessage("Something went wrong"/false)
   - setHasData = Function to call to set if the results has got data or not, if false an info message will be shown automatically, setHasData(true/false)
   - setInfoMessage = Function to call to set or remove an info message for the results, setInfoMessage({title: "Info title", text: "Info text"}/false)
   - setParams = Function to call to set extra params for the endpoint call, setParams({extraParam: "x"})
   - setIsLoading = Function to call to show or hide the loader for the results, setIsLoading(true/false)


### `ResultsContainerPresentation`
Data props
   - activeId = Id of the current active widget 
   - config = `results` presentation object
   - data = The repsonse data from the endpoint call
   - entitlements = Current user entitlement codes
   - triggerChildGetData = Incremented value every time the active widget is updated and the component should trigger a getData call

Functions props
   - getData = Function to call to trigger the data endpoint call
