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

|    Key    |     Default value     |     Type     |            Description            |
|-----------|-----------------|--------------|-----------------------------------|
|  `color`  |  ![#444444](https://placehold.it/15/444444/000000?text=+) #444           | string/`color`       |   Category colour                 |
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
|  `container`   |                 | object       |   Data handling config  |
|  `container.component`   |        | string/`ComponentDataContainer`     |   Determines which component should handle the data. Write a custom one or choose from predefined ones: DataContainer, ...  |
|  `container.endpoint`   |                 | string       |  The endpoint to fetch the data from. Ignored if container.component is a custom component   |
|  `presentation`   |                 | object       |  Visual presentation config   |
|  `entitlement`   |                 | string       |  Determines if the user can see the widgets content / add it to a workspace. If not defined - no user can do this, but it will still appear in the lists   |
|  `sidebar`   |                 | object       |  ...   |
|  `minW`   |      1           | int       |  The smallest width the widget can shrink to   |
|  `minH`   |      1           | int       |  The smallest height the widget can shrink to   |
|  `w`   |      4          | int       |  The initial width for the widget   |
|  `h`   |      5           | int       |  The initial height for the widget   |

### Icons
https://material.io/icons/

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
- `ComponentDataContainer`
