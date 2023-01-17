
## Main

```text
lunar-datepicker/
├── css/
│   ├── datepicker-1.0.10.min.css
│   ├── lunar-datepicker.css
│   └── lunar-datepicker.scss
├── js/
│   ├── jquery-3.6.3.min.js
│   ├── datepicker1.0.10.js 
│   └── lunar-datepicker-1.0.0.js
├── index.html
└── README.md
```

### Install

Include files CSS:
```css
<link rel="stylesheet" href="css/datepicker-1.0.10.min.css">
<link rel="stylesheet" href="css/lunar-datepicker.css">
```

Include files JS:
```js
<script src="jquery-3.6.3.min.js"></script>
<script src="js/datepicker1.0.10.js"></script>
<script src="https://kit.fontawesome.com/30b29e4428.js"></script> <!-- 請更新成自己的 icon -->
<script src="js/lunar-datepicker-1.0.0.js"></script>
```

### Usage

html:
```html
<div class="dateBox">
  <input data-toggle="datepicker" id="dataTage">
  <label for="dataTage"><i class="fa-solid fa-calendar-days"></i></label>
</div>
<div id="datepickerBox"></div>
```

JS:
```js
$(function () {
  $('[data-toggle="datepicker"]').datepicker({
    format: 'YYYY 年 MM 月 DD 日',
    date: new Date(), 
    autoPick: true, 
    container: '#datepickerBox',
    inline: true,
    weekStart: 7,
    yearFirs: true,
    filter: function() { 
      $('[data-view="day"] span').innerHTML == null ? setTimeout('funLunarData()') : '';
    },
  })
});
```

## Options

### format

- Type: `String`
- Default: `'mm/dd/yyyy'`
- Available date placeholders:
  - Year: `yyyy`, `yy`
  - Month: `mm`, `m`
  - Day: `dd`, `d`

參考樣式
- YYYY 年 MM 月 DD 日

### date

- Type: `Date` or `String`
- Default: `null`

- new Date(), // 預設當天日期

### autoPick

- Type: `Boolean`
- Default: `false`

input 一開始顯示預設日期

### container

- Type: `Element` or `String`(selector)
- Default: `null`

參考樣式
container: '#datepickerBox', // 月曆顯示位置

### inline

- Type: `Boolean`
- Default: `false`

月曆直接顯示

### startDate

- Type: `Date` or `String`
- Default: `null`

可以使用 new Date()等日期方式

### endDate

- Type: `Date` or `String`
- Default: `null`

可以使用 new Date()等日期方式

### weekStart

- Type: `Number`
- Default: `0`
- Options:
  - `0`: 星期日
  - `1`: 星期一
  - `2`: 星期二
  - `3`: 星期三
  - `4`: 星期四
  - `5`: 星期五
  - `6`: 星期六


  ### yearFirst

- Type: `Boolean`
- Default: `false`

年份是否放在前頭

### filter

- Type: `Function`
- Default: `null`
- Syntax: `filter(date, view)`
  - `date`: the date for checking.
  - `view`: the the current view, one of `day`, `month` or `year`.

Filter each date item. If return a `false` value, the related date will be disabled.


依據日期填加上農曆日期
```js
$().datepicker({
  filter: function() {
    $('[data-view="day"] span').innerHTML == null ? setTimeout('funLunarData()') : '';
  }
});
```