> 注意：此组件在性能较差的手机上，可能表现不是很理想，低配置手机请慎重使用。

[github 地址: https://github.com/mehaotian/t-color-picker](https://github.com/mehaotian/t-color-picker)
[插件市场地址：http://ext.dcloud.net.cn/plugin?id=412](http://ext.dcloud.net.cn/plugin?id=412)

我们在开发 `web` 应用的时候，想选择颜色，直接使用 `<input type="color">` 即可, 然而在 `uni-app` 中并没有选择器，需要我们去实现相关功能。

此组件基本全平台支持。（支付宝，百度，头条小程序理论上都支持，但是没有很细致的测试这几个平台）

**功能亮点**
- 全颜色选择，支持色相选择，透明度选择
- rgba 颜色显示 ，二进制颜色显示
- 可定义备选色
- 自定义默认颜色

**未实现**
- 只能选择，不能手动输入 （代码比较简单，需要可自行实现，有现成的方法可以调用）
- 颜色添加收藏 （可在备选色的基础上扩展，不会涉及到基本逻辑的改动）
- 已经实现 HSLA 颜色模式 ，但未做展示，可自行扩展
- 未实现拾色功能，将来可能也不会去实现，app 上这个功能可能不实用

**效果演示**
![color-picker.gif](https://upload-images.jianshu.io/upload_images/4472817-ce66f41e378b7d73.gif?imageMogr2/auto-orient/strip)

### 调用方式

*代码示例*
```html

<template>
	<view>
		<t-color-picker></t-color-picker>
	</view>
</template>
<script>
	import tColorPicker from '@/components/t-color-picker/t-color-picker.vue'
	export default {
		components: {
			tColorPicker
		}
	};
</script>

```

### 属性说明


|  属性名		|    类型	| 默认值				| 说明										|
| ---			| ---		| ---					| ---									|
| color			| Object	| {r: 0,g: 0,b: 0,a: 1}	|  颜色选择器初始颜色						|
| spare-color	| Object	|						|  备选色，格式为:[ {r: 0,g: 0,b: 0,a: 1}]	|
|confirm        | function	|						|  确认选择函数 ，返回值:event = {rgba:{r: 0,g: 0,b: 0,a: 1},hex:'#000000'}	|

### 事件说明

#### open()
打开颜色选择器，需要 `t-color-picker` 中声明 `ref` 属性


*完整使用示例*

```html


<template>
	<view class="t-page">
		<button @click="open">打开颜色选择器</button>
		<!-- 需要声明 ref  -->
		<t-color-picker ref="colorPicker" :color="color" @confirm="confirm"></t-color-picker>
	</view>
</template>
<script>
	import tColorPicker from '@/components/t-color-picker/t-color-picker.vue'
	export default {
		components: {
			tColorPicker
		},
		data() {
			return {
				color: {r: 255,g: 0,b: 0,a: 0.6}
			};
		},
		methods: {
			open(item) {
				// 打开颜色选择器
				this.$refs.colorPicker.open();
			},
			confirm(e) {
				console.log('颜色选择器返回值：'+ e)
			}
		}
	};
</script>


```



### 更新日志

#### v1.0.0
- 初次提交