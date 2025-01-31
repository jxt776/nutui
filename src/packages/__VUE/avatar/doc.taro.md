# Avatar 头像

### 介绍

用来代表用户或事物，支持图片、图标或字符展示。

### 安装

```javascript
import { createApp } from 'vue';
import { Avatar } from '@nutui/nutui';

const app = createApp();
app.use(Avatar);
```

### 基础用法

支持三种尺寸：small、normal、large

:::demo

```html
<template>
  <nut-avatar size="large">
    <img src="https://img12.360buyimg.com/imagetools/jfs/t1/143702/31/16654/116794/5fc6f541Edebf8a57/4138097748889987.png" />
  </nut-avatar>
  <nut-avatar size="normal">
    <img src="https://img12.360buyimg.com/imagetools/jfs/t1/143702/31/16654/116794/5fc6f541Edebf8a57/4138097748889987.png" />
  </nut-avatar>
  <nut-avatar size="small">
    <img src="https://img12.360buyimg.com/imagetools/jfs/t1/143702/31/16654/116794/5fc6f541Edebf8a57/4138097748889987.png" />
  </nut-avatar>
</template>
```

:::

### 头像形状

支持两种形状：square、round

:::demo

```html
<template>
  <nut-avatar shape="square"><My /></nut-avatar>
  <nut-avatar shape="round"><My /></nut-avatar>
</template>
```

:::

### 头像类型

支持三种类型：图片、Icon 以及字符

:::demo

```html
<template>
  <nut-avatar>
    <img src="https://img12.360buyimg.com/imagetools/jfs/t1/196430/38/8105/14329/60c806a4Ed506298a/e6de9fb7b8490f38.png" />
  </nut-avatar>
  <nut-avatar><My /></nut-avatar>
  <nut-avatar>王</nut-avatar>
</template>
```

:::

### 自定义颜色及背景色

Icon 和字符型可以自定义颜色及背景色

:::demo

```html
<template>
  <nut-avatar class="demo-avatar" bg-color="#FA2C19"><My color="#fff"/></nut-avatar>
  <nut-avatar color="rgb(245, 106, 0)" bg-color="rgb(253, 227, 207)">小明</nut-avatar>
</template>
```

:::

### 带徽标的头像

:::demo

```html
<template>
  <nut-badge value="8">
    <nut-avatar shape="square"><My /></nut-avatar>
  </nut-badge>
  <nut-badge dot>
    <nut-avatar shape="square"><My /></nut-avatar>
  </nut-badge>
</template>
```

:::

### 头像组合展现

:::demo

```html
<template>
  <nut-avatar-group span="-4">
    <nut-avatar>
      <img src="https://img12.360buyimg.com/imagetools/jfs/t1/196430/38/8105/14329/60c806a4Ed506298a/e6de9fb7b8490f38.png" />
    </nut-avatar>
    <nut-avatar><My /></nut-avatar>
    <nut-avatar color="rgb(245, 106, 0)" bg-color="rgb(253, 227, 207)">小明</nut-avatar>
  </nut-avatar-group>
  <nut-avatar-group
    max-count="3"
    max-color="#fff"
    max-bgColor="#498ff2"
  >
    <nut-avatar>
      <img src="https://img12.360buyimg.com/imagetools/jfs/t1/196430/38/8105/14329/60c806a4Ed506298a/e6de9fb7b8490f38.png" />
    </nut-avatar>
    <nut-avatar><My /></nut-avatar>
    <nut-avatar color="rgb(245, 106, 0)" bg-color="rgb(253, 227, 207)">小明</nut-avatar>
    <nut-avatar><My /></nut-avatar>
  </nut-avatar-group>
</template>
```

:::

### 组合头像可控制层级方向

:::demo

```html
<template>
  <nut-avatar-group
    max-count="3"
    zIndex="right"
    max-content="..."
  >
    <nut-avatar>
      <img src="https://img12.360buyimg.com/imagetools/jfs/t1/196430/38/8105/14329/60c806a4Ed506298a/e6de9fb7b8490f38.png" />
    </nut-avatar>
    <nut-avatar><My /></nut-avatar>
    <nut-avatar color="rgb(245, 106, 0)" bg-color="rgb(253, 227, 207)">U</nut-avatar>
    <nut-avatar><My /></nut-avatar>
  </nut-avatar-group>
</template>
```

:::

### 点击头像触发事件

:::demo

```html
<template>
  <nut-cell>
    <nut-avatar @click="handleClick"><My /></nut-avatar>
  </nut-cell>
</template>
<script lang="ts">
  import { reactive } from 'vue';
  export default {
    setup() {
      const handleClick = () => {
        console.log('触发点击头像');
      };

      return {
        handleClick
      };
    }
  }
</script>
```

:::

## API
### Avatar Props

| 字段     | 说明                                                        | 类型   | 默认值 |
| -------- | --------------------------------------------------------- | ------ | ------ |
| size     | 头像的大小，可选值为：`large`、`normal`、`small`，支持输入数字   | String ｜ Number | normal |
| shape    | 头像的形状，可选值为：`square`、`round `                      | String | round  |
| color    | 字体颜色                                     | String | #666   |
| bg-color | 背景色                                    | String | #eee   |

### AvatarGroup Props

| 字段     | 说明                                                             | 类型   | 默认值 |
| -------- | ---------------------------------------------------------------- | ------ | ------ |
| max-count    | 显示的最大头像个数   | String ｜ Number | - |
| max-content  | 头像数量超出时，会出现一个头像折叠元素，该元素内容可为`...`、`more`、`+N` | String | +N |
| size         | 头像的大小，可选值为：`large`、`normal`、`small`，支持直接输入数字   | String ｜ Number | normal |
| shape        | 头像的形状，可选值为：`square`、`round`        | String | round  |
| max-color    | 头像折叠元素的字体颜色                   | String | #666 |
| max-bg-color  | 头像折叠元素的背景色                    | String | #eee   |
| span         | 头像之间的间距               | String | -8   |
| zIndex       | 组合头像之间的层级方向，可选值为：`left`、`right`  | String | left     |
### Avatar Slots

|名称|描述|
|--|--|
|default|默认插槽，可放置图片、图标、文本等元素|