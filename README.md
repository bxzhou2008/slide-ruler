# fork [simbawus/slide-ruler](https://github.com/simbawus/slide-ruler.git) and customize (upside down ruler)

# Original version SlideRuler [Demo](https://wusb.github.io/slide-ruler)

[![Build Status](https://travis-ci.org/wusb/slide-ruler.svg?branch=master)](https://travis-ci.org/wusb/slide-ruler)
[![npm](https://img.shields.io/npm/v/slide-ruler.svg)](https://www.npmjs.com/package/slide-ruler)
[![npm](https://img.shields.io/npm/dt/slide-ruler.svg)](https://www.npmjs.com/package/slide-ruler)
[![npm](https://img.shields.io/npm/l/slide-ruler.svg)](https://www.npmjs.com/package/slide-ruler)

###### [中文 README](README-zh_CN.md)

## Features
- Developed with native javascript, doesn't rely on any frameworks and libraries.
- Customizable colors, sizes, precision, etc.
- Supports inertia and rebound for swiping meters.
- Friendly API for easy use.

| original      | customize     |
| :------------ | :------- |
!![example](https://i.loli.net/2018/06/27/5b3350dd2c4cc.gif) | ![demo2](https://raw.githubusercontent.com/bxzhou2008/slide-ruler/master/demo.png) |


## PropTypes

| Property      | Type     | Default      | Description            |
| :------------ | :------- | :----------- | :--------------------- |
| handleValue   | Function |              | get the return value   |
| end   | Function |              | event ended trigger   |
| canvasWidth   | Number   | screen width | ruler width            |
| canvasHeight  | Number   | 83           | ruler height           |
| heightDecimal | Number   | 35           | scale marks length     |
| heightDigit   | Number   | 18           | division marks length  |
| lineWidth     | Number   | 2            | marks width            |
| colorDecimal  | String   | #E4E4E4      | scale marks color      |
| colorDigit    | String   | #E4E4E4      | division marks color   |
| divide        | Number   | 10           | division length of px  |
| precision     | Number   | 1            | division value         |
| fontSize      | Number   | 20           | scale fontSize         |
| fontColor     | String   | #666666      | scale fontColor        |
| fontMarginTop | Number   | 35           | font margin to the top |
| maxValue      | Number   | 230          | max value              |
| minValue      | Number   | 100          | min value              |
| currentValue  | Number   | 100          | current value          |

## Getting Started

### Install

```shell
yarn add slide-ruler --dev
```

### Usage Example

- **Native JavaScript**

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8" />
    <meta name="author" content="simbawu" />
    <title>Digital Keyboard</title>
  </head>
  <body>
    <div id="values"></div>
    <div id="app"></div>
    <script src="./slide-ruler.js"></script>
  </body>
</html>
```

```javascript
//slide-ruler.js
import SlideRuler from 'slide-ruler';

function handleValue(value){
  console.log(value); //SlideRuler return value
  document.querySelector('#values').innerHTML = value;
}

new SlideRuler(
    {
        el: document.querySelector('#app'),
        maxValue: 230,
        minValue: 100,
        currentValue: 180
        handleValue: handleValue,
        precision: 1
    }
);
```

- **Vue**

```js
<template>
  <div></div>
</template>
<script>
import SlideRuler from 'slide-ruler';
export default {
  mounted () {
    this._renderSlideRuler();
  },
  methods: () {
    _renderSlideRuler() {
    	return new SlideRuler (
          {
            el: this.$el,
            maxValue: 230,
            minValue: 100,
            currentValue: 180
            end: this.end,
            handleValue: this.handleValue,
            precision: 1
          }
        );
    },

    handleValue(value) {
      console.log(value); //SlideRuler return value
    },
    end(value){
      console.log(value); //结束触发
    }
  }
}
</script>
```

## How to Contribute

Anyone and everyone is welcome to contribute to this project. The best way to start is by checking our [open issues](https://github.com/bunsen/slide-ruler/issues),[submit a new issues](https://github.com/bunsen/slide-ruler/issues/new?labels=bug) or [feature request](https://github.com/bunsen/slide-ruler/issues/new?labels=enhancement), participate in discussions, upvote or downvote the issues you like or dislike.

## License

[**The MIT License**](http://opensource.org/licenses/MIT).
