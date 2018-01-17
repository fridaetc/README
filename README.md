<h1 align="center">
   <img height="72" width="150" src="/AgilityLogoInverted.svg">
</h1>

- [Config](#config)
   - [Categories](#categories)
   - [Widgets](#widgets)
- Icons
- Colors


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
|  `color`  |  #444           | string       |   Category colour                 |
|  `name`   |                 | string       |   Category title                  |
|  `icon`   |                 | string       |   Category icon                   |
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
|  `category`  | | string (`uniqueCategoryKey`) | Sets the widgets category which appears in widget list and label of the widget |
|  `name`   |                 | string       |   Widgets default title (can be renamed by user)  |
