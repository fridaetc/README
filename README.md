<h1 align="center">
   <img height="72" width="150" src="/AgilityLogoInverted.svg">
</h1>

- [Config](#config)
   - [Categories](#categories)
   - [Widgets](#widgets)
- [Icons](#icons)
- [Colors](#colors)

## Config
Configuration objects
```
{
   categories,
   widgets,
   filters,
   options,
   messages,
   results
}
```

### Categories
```
categories: {
   uniqueCategoryKey: {
      key,
      ...
   },
   ...
}
```

|    Key    |     Default     |     Type     |            Description            |
|-----------|-----------------|--------------|-----------------------------------|
|  `color`  |  #444           | string/`color`       |   Category colour                 |
|  `name`   |                 | string       |   Category title                  |
|  `icon`   |                 | `icon`       |   Category icon                   |
|  `label`  | false           | boolean      |   Defines if the category label should be visible in the bottom left corner of the widgets|

### Widgets
```
widgets: {
   uniqueWidgetKey: {
      key,
      ...
   },
   ...
}
```

|    Key    |     Default     |     Type     |            Description            |
|-----------|-----------------|--------------|-----------------------------------|
|  `category`  | | `uniqueCategoryKey` | Sets the widgets category which appears in widget list and label of the widget |
|  `name`   |                 | string       |   Widgets default title (can be renamed by user)  |

### Icons
|    Name    |     Icon     | 
|------------|---------------|
|  `account child`  |   MEH     |

### Colors
|    Name    |     Color     | 
|------------|---------------|
|  `slime`  |   #B5CC18     |
