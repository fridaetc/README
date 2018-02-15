- Config
   - Categories
   - Widgets
   - Filters
   - Options
   - Results
- Icons
- Colors
- Components

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

|    Key    | Required  |    Default value     |     Type     |            Description            |
|-----------|-----------|-----------------|--------------|-----------------------------------|
|  `name`   |  Yes |               | string       |   Category title                  |
|  `color`  | | ![#444444](https://placehold.it/15/444444/000000?text=+) #444           | string(`color`)       |   Category colour, from list of predefined colours or hex like #000000                 |
|  `icon`   |       |          | string(`icon`)       |   Category icon, from list of predefined icons                   |
|  `label`  |     |           | boolean      |   Defines if the category label should be visible in the bottom left corner of the widgets|


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

|    Key    | Required  |     Default     |     Type     |            Description            |
|-----------|-----------|-----------------|--------------|-----------------------------------|
|  `category` | Yes | | string(`uniqueCategoryKey`) | Sets the widgets category which appears in widget list and label of the widget |
|  `name`   | Yes |               | string       |   Widgets default title (can be renamed by user)  |
|  `container`   |  Yes   |            | object       |   Data handling config  |
|  `container.component`   | Yes |      | string/function(`ContainerComponent`)     |   Which component should handle the data. Write a custom one or choose from predefined ones: DataContainer, ...  |
|  `container.endpoint`  | If container.component = string | | string  |  The endpoint to fetch the data from. Ignored if container.component is a custom component   |
|  `presentation`   |  If container.component = string   |            | object       |  Visual presentation config   |
|  `presentation.component` | If container.component = string |  | string/function(`PresentationComponent`)  |  Which component should present the data. Write a custom one or choose from predefined ones: BarChart, PieChart, Table ... Ignored if container.component is a custom component  |
|  `presentation.chartType`  | | | string |  Used when presentation.component is predefined. Defines what type of chart to show in the homepage thumbnails. Choose from predefined ones: bar, pie, column, map   |
|  `presentation.chartTitle`  | |  | string    |  Used when presentation.component is predefined and a chart. Set the y title and tooltip title of the chart  |
|  `presentation.chartColors`  | | category.color |  array[string(`color`)]   |  Used when presentation.component is predefined. Sets the widget content color (if applicable)  |
|  `entitlement`   | Yes | | string  |  Determines if the user can see the widgets content / add it to a workspace  |
|  `exportEntitlement` |  |  | string  |  Determines if the user can see export widgets data  |
|  `sidebar`   |   |              | object       |  What will be shown in the widget tab in the sidebar   |
|  `sidebar.filters`   | |     | boolean  |  Determines if to show filter section in sidebar, which displays filters defined in the filter config. If not defined or false and container.component is predefined, data will be presented straight away in the widget rather than clicking "run" from sidebar   |
|  `sidebar.options`|  | |  array[string(`uniqueOptionKey`)]  |  Shows options section in sidebar populated with content from options config   |
|  `minW`   |   |   1           | int       |  The smallest width the widget can shrink to   |
|  `minH`   |  |    1           | int       |  The smallest height the widget can shrink to   |
|  `w`   |    |  4          | int       |  The initial width for the widget   |
|  `h`   |   |   5           | int       |  The initial height for the widget   |


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

|    Key    | Required |     Default     |     Type     |            Description            |
|-----------|----------|-----------------|--------------|-----------------------------------|
|  `endpoints`  | Yes | | object | Endpoints |
|  `endpoints.filterValues`  | If filters = defined | | string | Endpoint to populate all the filter components with values |
|  `endpoints.totalResults`  | if totalResults = defined | | string | Endpoint to get the stats at the top of the sidebar |
|  `totalResults`  | | | array[object{key, name}] | What to display in the stats, key comes from the endpoints response data |



Filters.filters:

|    Key    | Required|     Default     |     Type     |            Description            |
|-----------|----------|-----------------|--------------|-----------------------------------|
|  `name`  | Yes | | string | Title of the filter |
|  `category`  | Yes | | string(`uniqueCategoryKey`) | Sets the filters category which appears in filters list |
|  `component` | Yes | | | Which component should present the filter. Write a custom one or choose from predefined: Dropdown, Checkbox, NumberRange, SliderRange ...  |
|  `autoComplete`  |  | | boolean | If filter should have autocomplete, only works when component is Dropdown |
|  `autoCompleteEndpoint`  | If autoComplete = true | | string | Endpoint to populate the dropdown filter with autocomplete results |
|  `wildcard`  |  | | boolean | If filter is autocomplete and Dropdown, option to add wildcard search from the search string  |



### Options
Creates dropdowns with widget settings
```
options: {
   uniqueOptionKey: {
      key,
      ...
   },
   ...
}
```

|    Key    |     Default     |     Type     |            Description            |
|-----------|-----------------|--------------|-----------------------------------|
|  `name`  | | string | Title of the option  |
|  `defaultValue`  | | string | Default selected value of the dropdown |
|  `options`  | | array[{text, value}] | Options for the dropdown |


### Results
Settings for the sticky results table
```
results: {
   key,
   ...
}
```

|    Key    |     Default     |     Type     |            Description            |
|-----------|-----------------|--------------|-----------------------------------|
|  `title`  | | string | Title of the results |
|  `description`  | | string | Description of the results |
|  `size`  | 8 | string | Table rows per page |
|  `columns`  | w = 16/columns.length | array[{name, key, w}] | Which fields to show in the results. w = width of the table cell based on a 16 grid |
|  `endpoint`  | | string | The endpoint to fetch the tables data from |
|  `entitlement`  | | string | Determines if the user can see the table. If not defined - No user can do this |

### Icons
https://material.io/icons/ (future)

### Colors
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

### Components
Custom components access to props via this.props.x (temp)
1. `ComponentContainer`
   - config = `uniqueWidgetKey` object
   - widget = ...
   - id = this widget id
   - query = widget active query
   - widgetContentUpdate = function(popupcomponent, errors, info, hasdata)
   - workspaceId = this workspace id

2. `ComponentPresentation`
   - data = data from call
   - all of ComponentContainer props
