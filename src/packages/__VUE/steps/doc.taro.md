# Steps 步骤条

### 介绍

拆分展示某项流程的步骤，引导用户按流程完成任务或向用户展示当前状态。

### 安装

```javascript
import { createApp } from 'vue';
import { Steps, Step  } from '@nutui/nutui-taro';

const app = createApp();
app.use(Steps);
app.use(Step);
```

### 基础用法

:::demo

```html
<template>
  <nut-steps :current="current1" @click-step="handleClickStep">
    <nut-step title="步骤一">
      1
      <template #title>步骤一</template>
    </nut-step>
    <nut-step title="未开始">2</nut-step>
    <nut-step title="未开始">3</nut-step>
    <nut-step title="未开始">4</nut-step>
  </nut-steps>
</template>
<script>
  import { reactive, toRefs } from 'vue';
  export default {
    setup() {
      const state = reactive({
        current1: 1,
      });
      const handleClickStep = (index: number) => {
        console.log(index)
      };
      return { ...toRefs(state), handleClickStep };
    }
  };
</script>
```
:::

### 标题和描述信息

:::demo

```html
<template>
  <nut-steps :current="current2">
    <nut-step title="已完成" content="步骤描述">1</nut-step>
    <nut-step title="进行中" content="步骤描述">2</nut-step>
    <nut-step title="未开始" content="步骤描述">3</nut-step>
  </nut-steps>
</template>
<script>
  import { reactive, toRefs } from 'vue';
  export default {
    setup() {
      const state = reactive({
        current2: 1,
      });
      return { ...toRefs(state) };
    }
  };
</script>
```

:::

### 自定义图标

:::demo

```html
<template>
  <nut-steps current="1">
    <nut-step title="已完成">
      <template #icon><Service /></template>
    </nut-step>
    <nut-step title="进行中">
      <template #icon><People /></template>
    </nut-step>
    <nut-step title="未开始">
      <template #icon><Location2 /></template>
    </nut-step>
  </nut-steps>
</template>
```

:::

### 竖向步骤条

:::demo

```html
<template>
  <nut-steps direction="vertical" current="2">
    <nut-step title="已完成" content="您的订单已经打包完成，商品已发出">1</nut-step>
    <nut-step title="进行中" content="您的订单正在配送途中">2</nut-step>
    <nut-step title="未开始" content="收货地址为：北京市经济技术开发区科创十一街18号院京东大厦">3</nut-step>
  </nut-steps>
</template>
```

:::

### 点状步骤和垂直方向

:::demo

```html
<template>
  <nut-steps direction="vertical" progress-dot current="2">
    <nut-step title="已完成" content="您的订单已经打包完成，商品已发出">1</nut-step>
    <nut-step title="进行中" content="您的订单正在配送途中">2</nut-step>
    <nut-step title="未开始">
      3
      <template #content>
        <p>收货地址为：</p>
        <p>北京市经济技术开发区科创十一街18号院京东大厦</p>
      </template>
    </nut-step>
  </nut-steps>
</template>
```

:::




## API

### Steps Props

| 参数                   | 说明                                                        | 类型           | 默认值      |
| ---------------------- | ----------------------------------------------------------- | -------------- | ----------- |
| direction	             | 	显示方向，`horizontal`,`vertical`  | string        | `horizontal`  | 
| current	               | 	当前所在的步骤           | number、string        | `0`      |
| progress-dot            |  点状步骤条     | boolean | `false`         |

### Steps Events

| 事件名 | 说明           | 回调参数     |
|--------|----------------|--------------|
| click-step  | 点击步骤的标题或图标时触发 | index: number |

### Step Props

| 参数           | 说明                   | 类型     | 默认值      |
| ---------------- | ---------------------- | ------------ | ----------- |
| title            | 流程步骤的标题         | string | `步骤` |
| content          | 流程步骤的描述性文字(支持 html 结构)       | string | `步骤描述` |

### Step Slots

| 参数           | 说明                   |
| ---------------- | ---------------------- |
| title            | 步骤标题         |
| content          | 步骤内容       |
| icon             | 步骤图标       |
