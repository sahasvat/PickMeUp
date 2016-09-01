## PickMeUp - jQuery datepicker plugin

Really simple, powerful and customizable datepicker.

Author - Nazar Mokrynskyi

Based on DatePicker by Stefan Petre

Browser support:
* IE 10+
* Opera 12.1+
* Latest versions of Firefox and Chrome

## [Demo](http://nazar-pc.github.io/PickMeUp)

## Getting started
You need only 2 files: `js/jquery.pickmeup.min.js` and `css/pickmeup.css`.

The plugin can also be loaded as AMD or CommonJS module.

Then you can apply datepicker to any element:
```javascript
pickmeup('.date');
```
Global default options are stored in `pickmeup.defaults`

They can be redefined during initialization:
```javascript
pickmeup('.date', {
	format	: 'Y-m-d'
});
```

or with data-attributes with `pmu-` prefix:
```html
<div class="date" data-pmu-format="Y-m-d"></div>
```

## Twitter Bootstrap integration
For Twitter Bootstrap integration you do not need to include style file, but you need to include `jquery.pickmeup.twitter-bootstrap.js` instead,
that will read settings of current Bootstrap theme and apply them to PickMeUp, so that it will look similar to native Bootstrap elements.

To apply integrated version, replace `pickmeup` with `pickmeup_twitter_bootstrap` in initialization:
```javascript
$('.date').pickmeup_twitter_bootstrap();
```
All options and events are the same.

## UIkit integration
For UIkit integration you do not need to include style file, but you need to include `jquery.pickmeup.uikit.js` instead,
that will read settings of current UIkit theme and apply them to PickMeUp, so that it will look similar to native UIkit elements.

To apply integrated version, replace `pickmeup` with `pickmeup_uikit` in initialization:
```javascript
$('.date').pickmeup_uikit();
```
All options and events are the same.


## Configuration options
| Option          | Value                             | Default          | Description                                                                                                          |
|-----------------|-----------------------------------|------------------|----------------------------------------------------------------------------------------------------------------------|
| date            | array/number/object/string        | new Date         | Selected date after initialization. Can be single date string/object or array depending on selection mode            |
| default_date    | boolean                           | true             | If `false` will keep empty value until date selected                                                                 |
| current         | number/object/string              | date             | Represents date that will be in the center of rendered calendar, defaults to `date` option's value                   |
| flat            | boolean                           | false            | Whatever if the date picker is appended to the element or triggered by an event                                      |
| first_day       | 0/1                               | 1                | First day of week: 0 - Sunday, 1 - Monday                                                                            |
| prev            | string                            | &#9664;          | Previous button content                                                                                              |
| next            | string                            | &#9654;          | Next button content                                                                                                  |
| mode            | single/multiple/range             | single           | Date selection mode                                                                                                  |
| select_day      | boolean                           | true             | Allow or deny days selection                                                                                         |
| select_month    | boolean                           | true             | Allow or deny months selection                                                                                       |
| select_year     | boolean                           | true             | Allow or deny year selection                                                                                         |
| view            | days/months/years                 | days             | View mode after initialization                                                                                       |
| calendars       | int                               | 1                | Number of calendars, that will be rendered                                                                           |
| format          | string                            | d-m-Y            | Date format (aAbBCdeHIjklmMpPsSuwyY are supported)                                                                   |
| title_format    | string                            | B, Y             | Date format for calendar title in days view (aAbBCdeHIjklmMpPsSuwyY are supported)                                   |
| position        | top/right/bottom/left             | bottom           | Date picker's position relative to the triggered element                                                             |
| trigger_event   | string                            | click touchstart | Event to trigger the date picker                                                                                     |
| class_name      | string                            |                  | Class to be added to root datepicker element                                                                         |
| hide_on_select  | boolean                           | false            | If `true` - datepicker will be hidden after selection (for range mode allows to select first and last days)          |
| min             | number/object/string              |                  | Min date available for selection                                                                                     |
| max             | number/object/string              |                  | Max date available for selection                                                                                     |
| separator       | string                            | ` - `            | Is used for joining separate dates in multiple mode and first/last dates in range mode                               |
| locale          | object                            |                  | Object, that contains localized days of week names and months. See [Localization](#localization)
## Events callbacks
`this` in any callback will be the same element, on which pickmeup() was called.
Events are specified as regular options:

##### object render (date)
Triggered on day element rendering, accepts date as argument and may return object with next properties:
* `selected`: if `true` - date will be selected
* `disabled`: if `true` - date will be disabled
* `class_name`: will be added to class of day element

##### change (formatted_date)
Triggered at date change, accepts formatted date as argument

##### before_show ()
Triggered before showing

##### bool show ()
Triggered at showing, if not `true` returned - datepicker will not be shown

##### bool hide ()
Triggered at hiding, if not `true` returned - datepicker will not be hidden

##### fill()
Triggered after filling of PickMeUp container with new markup of days, months, years.
May be needed for inner datepicker markup editing.

## Methods
Methods allows external control on datepicker

##### Hide
```javascript
pickmeup('.date').hide();
```

##### Show
```javascript
pickmeup('.date').show();
```

##### Prev
```javascript
pickmeup('.date').prev();
```

##### Next
```javascript
pickmeup('.date').next();
```

##### Get date
```javascript
pickmeup('.date').get_date(formatted);
```
`formatted` - boolean or string (default `false`)
* `false` - `Date` object
* `true` - string formatted in accordance with `format` option
* string is used to specify custom format instead if given during initialization

##### Set date
```javascript
pickmeup('.date').set_date(date);
```
`date` - can be single date string/object or array depending on selection mode

##### Clear multiple selection
```javascript
pickmeup('.date').clear();
```

##### Update datepicker
```javascript
pickmeup('.date').update();
```

##### Destroy datepicker
Destroys PickMeUp instance, removes created markup, restores everything that was changed to original state.
```javascript
pickmeup('.date').destroy();
```

## Localization
Sample object for English language:
````javascript
{
	days: ['Sunday', 'Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday', 'Saturday', 'Sunday'],
	daysShort: ['Sun', 'Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun'],
	daysMin: ['Su', 'Mo', 'Tu', 'We', 'Th', 'Fr', 'Sa', 'Su'],
	months: ['January', 'February', 'March', 'April', 'May', 'June', 'July', 'August', 'September', 'October', 'November', 'December'],
	monthsShort: ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', 'Jul', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec']
}
````

Russian:
````javascript
{
	days: ['Воскресенье', 'Понедельник', 'Вторник', 'Среда', 'Четверг', 'Пятница', 'Суббота', 'Воскресенье'],
	daysShort: ['Вс', 'Пн', 'Вт', 'Ср', 'Чт', 'Пт', 'Сб', 'Вс'],
	daysMin: ['Вс', 'Пн', 'Вт', 'Ср', 'Чт', 'Пт', 'Сб', 'Вс'],
	months: ['Январь', 'Февраль', 'Март', 'Апрель', 'Май', 'Июнь', 'Июль', 'Август', 'Сентябрь', 'Октябрь', 'Ноябрь', 'Декабрь'],
	monthsShort: ['Янв', 'Фев', 'Мар', 'Апр', 'Май', 'Июн', 'Июл', 'Авг', 'Сен', 'Окт', 'Ноя', 'Дек']
}
````

## Other
Current options (for whatever reason) can be accessed as `element.pickmeup.__pickmeup.options`.

Root pickmeup element can be accessed as `element.pickmeup`.

## Touch devices
PickMeUp doesn't include complete support for touch devices, only naive implementation.

If you need proper support for touch devices, you can use [jTAP](https://github.com/BR0kEN-/jTap) jQuery plugin and set `trigger_event` to `click tap`.

## Styling
If you want other colors - just change several variables in scss file.

To change size - adjust `font-size` for root datepicker element, everything will scale nicely.

## Contribution
Feel free to create issues and send pull requests, they are highly appreciated!

Before reporting an issue, be so kind to prepare reproducible example on jsfiddle.net, please.

You can start with working demo of latest stable version of PickMeUp: [jsfiddle.net/0kg5jL3p](https://jsfiddle.net/0kg5jL3p/)

## License
MIT License, see license.txt
