# 基于 [simbawus/slide-ruler](https://github.com/simbawus/slide-ruler.git) 定制而来，上下颠倒标尺，添加end钩子 
# 原版本的 SlideRuler [Demo](https://wusb.github.io/slide-ruler)

[![Build Status](https://travis-ci.org/wusb/slide-ruler.svg?branch=master)](https://travis-ci.org/wusb/slide-ruler)
[![npm](https://img.shields.io/npm/v/slide-ruler.svg)](https://www.npmjs.com/package/slide-ruler)
[![npm](https://img.shields.io/npm/dt/slide-ruler.svg)](https://www.npmjs.com/package/slide-ruler)
[![npm](https://img.shields.io/npm/l/slide-ruler.svg)](https://www.npmjs.com/package/slide-ruler)

###### [README in English](README.md)

- 原生 js 开发、不依赖任何框架和库的轻量级移动端数字键盘
- 可自定义尺子颜色、尺寸及精度等
- 支持惯性及弹性
- API 简洁，非常好上手

| 原版      | 定制后     |
| :------------ | :------- |
!![example](https://i.loli.net/2018/06/27/5b3350dd2c4cc.gif) | ![demo2](https://raw.githubusercontent.com/bxzhou2008/slide-ruler/master/demo.png) |


## 属性

| Property      | Type     | Default      | Description              |
| :------------ | :------- | :----------- | :----------------------- |
| handleValue   | Function |              | 获取尺子当前值           |
| end   | Function |              | 滚动结束触发          |
| canvasWidth   | Nubmer   | screen width | 尺子宽度                 |
| canvasHeight  | Nubmer   | 83           | 尺子高度                 |
| heightDecimal | Nubmer   | 35           | 长刻度线高度             |
| heightDigit   | Nubmer   | 18           | 短刻度线高度             |
| lineWidth     | Nubmer   | 2            | 刻度线宽度               |
| colorDecimal  | String   | #E4E4E4      | 长刻度线颜色             |
| colorDigit    | String   | #E4E4E4      | 短刻度线颜色             |
| divide        | Nubmer   | 10           | 两个刻度线之间的像素宽度 |
| precision     | Nubmer   | 1            | 最小刻度单位             |
| fontSize      | Nubmer   | 20           | 刻度字体大小             |
| fontColor     | String   | #666666      | 刻度字体颜色             |
| fontMarginTop | Nubmer   | 35           | 刻度字体与上边界距离     |
| maxValue      | Nubmer   | 230          | 尺子最大值               |
| minValue      | Nubmer   | 100          | 尺子最小值               |
| currentValue  | Nubmer   | 100          | 尺子当前值               |

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
  mounted (){
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
            handleValue: this.handleValue,
            end: this.end,
            precision: 1
          }
        );
    },

    handleValue(value) {
      console.log(value); //每次变动触发
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
