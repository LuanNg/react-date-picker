# React Ultra Date Picker
An iOS like, comprehensive date picker component for React.

If you are looking for a React Date Picker working on mobile platforms, this one would be a good choice. After browsing a lot of React Date Picker projects on GitHub, I found that most of them are PC-oriented, so I decided to write one for mobile platforms. This is how [React Ultra Select][1] and [React Ultra Date Picker][2] come.

This component depends on [React Ultra Select][1], so scrolling also relies on its version. You can change UltraSelect's version to use different scrolling features. 1.0.x for iscroll-scrolling and 1.1.x for div-scrolling. Default uses iscroll-scrolling.

# Features

- **Supporting 4 Types of Date Picker**

	- `date`

		Default type, you can select year, month and date with this type.

	- `datetime`

		You can select year, month, date, hour and minute with this type.

	- `time`

		You can select hour and minute with this type.

	- `month`

		You can select year and month with this type.

- **Precise Date Range(aka min date and max date)**

	Comprehensive and precise support of date range for all Date Picker types. Also supports out-of-range detection.

- **24-hour System and 12-hour System**

	Both two time system are supported.

- **Flexible Locale Configurations**

	Provides a very convenient API `addLocaleConfig` for custom locale config. Using this API, you can not only arrange order, but also decide how each year/month/date/ampm/hour/minute element is displayed.

- **Selection Events**

	Supports `onSelect` and `onDidSelect` events.

# How to use

```
npm i react-ultra-date-picker --save
```

Using it in your project:
```js
import React, { Component } from 'react'
import ReactDOM from 'react-dom'
import DatePicker from 'react-ultra-date-picker'

class SomeComponent extends Component {
	render() {
		return <DatePicker></DatePicker>
	}
}
```

# Props

## `dateStringProp`

`dateStringProp` is used as a constructor parameter of JavaScript `Date` Object. It can either be a number, or a string with [RFC2822 Section 3.3][6], [ISO-8601][5] format or simply `dd:dd` format.

- Number

    A positive or negative number representing the number of milliseconds passed from 1970-01-01.

- String of [RFC2822 Section 3.3][6]

    A string like `Sat Jul 30 2016 18:17:37 GMT+0800 (CST)`, which can be generated by `Date.toString()` or `Date.toDateString()`

- String of [ISO-8601][5]

    A string like `2016-07-30T10:18:43.422Z`, which can be generated by `Date.toJSON()`. Note that `Date.toJSON()` will return a UTC time.

- String of `dd:dd` format

    You should only use this format with prop `type=time`, and `dd:dd` is in 24-hour time system.

## Optional Props

 <table>
    <thead>
        <tr>
            <td><b>Prop Name</b></td>
            <td><b>Default Value</b></td>
            <td><b>Type</b></td>
            <td><b>Description</b></td>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>`min`</td>
            <td>`'01 Jan 1970 00:00'`</td>
            <td>`dateStringProp`</td>
            <td>Minimum date you can select.</td>
        </tr>
        <tr>
            <td>`max`</td>
            <td>`'19 Jan 2038 03:14'`</td>
            <td>`dateStringProp`</td>
            <td>Maximum date you can select.</td>
        </tr>
        <tr>
            <td>`defaultDate`</td>
            <td>`null`</td>
            <td>`dateStringProp`</td>
            <td>Default selected date.</td>
        </tr>
        <tr>
            <td>`type`</td>
            <td>`'date'`</td>
            <td>One of `'date'`, `'datetime'`, `'month'` and `'time'`</td>
            <td>Decide which type of date to select.</td>
        </tr>
        <tr>
            <td>`locale`</td>
            <td>`'en'`</td>
            <td>One of `'en'` or `'zh-cn'`, or locale name added by `addLocaleConfig`</td>
            <td>Tells which date locale configuration to use.</td>
        </tr>
        <tr>
            <td>`use24hours`</td>
            <td>`false`</td>
            <td>Boolean</td>
            <td>Whether to use 24-hour system or not.</td>
        </tr>
        <tr>
            <td>`title`</td>
            <td>`null`</td>
            <td>String</td>
            <td>Title for the selection panel.</td>
        </tr>
    </tbody>
 </table>

# Props for [React Ultra Select][1]

Since this component relies on [React Ultra Select][1], you can pass these props to it:

- `rowsVisible`
- `rowHeight`
- `rowHeightUnit`
- `backdrop`
- `disabled`
- `useTouchTap`
- `isOpen`

# Events/Callbacks

React Ultra Date Picker shares same events/callbacks with React Ultra Select:


- `onOpen()`

    Will be called when the selection panel shows up.

- `onClose()`

    Will be called when the selection panel hides.

- `onConfirm()`

    Will be called when the confirm button or backdrop is clicked.

- `onCancel()`

    Will be called when the cancel button is clicked.

- `onDidSelect(date)`

    Will be called when scrolling stops, useful for real-time selection. `date` is the current selected date.

- `onSelect(date)`

    Will be called when scrolling and selected value is changed, useful for playing sound effects or so. `date` is the current selected date.

# Functions

- `addLocaleConfig(name, config)`

	Adding a locale configuration to the Date Picker, so you can specify `locale` other than `en` and `zh-cn`. The config keys includes:

     <table>
        <thead>
            <tr>
                <td><b>Key</b></td>
                <td><b>Type</b></td>
                <td><b>Description</b></td>
                <td><b>Example Value</b></td>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>`order`</td>
                <td>Array</td>
                <td>The order of `year`, `month`, `date`, `ampm`, `hour` and `minute` in selection</td>
                <td>`['month', 'date', 'year', 'hour', 'minute', 'ampm']`</td>
            </tr>
            <tr>
                <td>`year`</td>
                <td>Function</td>
                <td>A function generates `year` string.</td>
                <td>`year => year`</td>
            </tr>
            <tr>
                <td>`month`</td>
                <td>Function</td>
                <td>A function generates `month` string.</td>
                <td>`month => month + 1`</td>
            </tr>
            <tr>
                <td>`date`</td>
                <td>Function</td>
                <td>A function generates `date` string.</td>
                <td>`date => date`</td>
            </tr>
            <tr>
                <td>`am`</td>
                <td>String</td>
                <td>A string for `am`, probably in different languages.</td>
                <td>`'AM'`</td>
            </tr>
            <tr>
                <td>`pm`</td>
                <td>String</td>
                <td>A string for `pm`, probably in different languages.</td>
                <td>`'PM'`</td>
            </tr>
            <tr>
                <td>`hour`</td>
                <td>Function</td>
                <td>A function generates `hour` string.</td>
                <td>`(hour, use24hours) => hour`</td>
            </tr>
            <tr>
                <td>`minute`</td>
                <td>Function</td>
                <td>A function generates `minute` string.</td>
                <td>`minute => minute`</td>
            </tr>
            <tr>
                <td>`confirmButton`</td>
                <td>String</td>
                <td>A string for the confirm button label, probably in different languages.</td>
                <td></td>
            </tr>
            <tr>
                <td>`cancelButton`</td>
                <td>String</td>
                <td>A string for the cancel button label, probably in different languages.</td>
                <td></td>
            </tr>
            <tr>
                <td>`dateLabel`</td>
                <td>Function</td>
                <td>A function accepts current selected date and generates display string.</td>
                <td>`(outOfRange, date, type, use24) => date.toJSON()`</td>
            </tr>
        </tbody>
     </table>

	For example, adding a Japanese(`ja`) locale config would be like below:

	```js
	import DatePicker,{addLocaleConfig, padStartWith0, translateHour} from 'react-ultra-date-picker'

    const jaConfig = {
        order: ['year', 'month', 'date', 'ampm', 'hour', 'minute'],
        year: year => `${year}年`,
        month: month => `${month+1}月`,
        date: date => `${date}日`,
        am: '朝',
        pm: '午後',
        hour: translateHour,
        minute: minute => padStartWith0(minute),
        confirmButton: '決定します',
        cancelButton: 'キャンセル',
        dateLabel: (outOfRange, date, type, use24) => {
            if (outOfRange) {
                return '日付を範囲で選択されていません'
            }
            switch (type) {
                case 'time':
                    return `${use24 ? '' : (date.getHours() < 12 ? jaConfig.am : jaConfig.pm)}${jaConfig.hour(date.getHours(), use24)}:${jaConfig.minute(date.getMinutes())}`
                case 'month':
                    return `${jaConfig.year(date.getFullYear())}${jaConfig.month(date.getMonth())}`
                case 'datetime':
                    return `${jaConfig.year(date.getFullYear())}${jaConfig.month(date.getMonth())}${jaConfig.date(date.getDate())} ${use24 ? '' : (date.getHours() < 12 ? jaConfig.am : jaConfig.pm)}${jaConfig.hour(date.getHours(), use24)}:${jaConfig.minute(date.getMinutes())}`
                case 'date':
                    return `${jaConfig.year(date.getFullYear())}${jaConfig.month(date.getMonth())}${jaConfig.date(date.getDate())}`
                default:
                    break
            }
        }
    }
    addLocaleConfig('ja', jaConfig)
	```

- `padStartWith0(num)`

	Pad a number smaller than 10 with a `0` at the start.

- `daysInMonth(year, month)`

	Calculates how many days in given year and month. Referenced from [StackOverflow][4]. Returns a number.

- `isPm(date)`

	Whether a given date is in p.m. or not. Returns a Boolean.

- `translateHour(hour, use24hours)`

    Translate an hour number to correct number according to the `use24hour` parameter with padding zero if needed.

- `DatePicker.date`

    Get the current selected date, a javascript `Date` Object will be returned. You can call `getFullYear()`, `getMonth()`, `getDate()`, `getHour()` or `getMinute()` depending on your needs. Remember to attach `ref` to `<DatePicker>`.

    ```js
    this.refs.datePicker.date
    ```

# Examples

- Online

	Open <https://swenyang.github.io/react-date-picker> to see online demo.

- Local

	Clone this repo, and run `npm run examples`. Then navigate to <http://localhost:8080> to see examples.

# TODO

- [x] Bugs on switching `use24hours` props; bugs on switching `locale` props

- Add more language configurations and export them to chunks

- Implementing more features in the web APIs of the INPUT DATE elemnent

[1]: https://github.com/swenyang/react-ultra-select
[2]: https://github.com/swenyang/react-date-picker
[3]: https://webpack.github.io
[4]: http://stackoverflow.com/questions/315760/what-is-the-best-way-to-determine-the-number-of-days-in-a-month-with-javascript
[5]: https://www.w3.org/TR/NOTE-datetime
[6]: http://tools.ietf.org/html/rfc2822#section-3.3
[7]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date/parse