<template>
	<view class="t-page">
		<view class="button" @click="open" :style="{ background: 'rgba(' + rgba.r + ',' + rgba.g + ',' + rgba.b + ',' + rgba.a + ')' }">修改按钮背景色</view>
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
				color: {
					r: 0,
					g: 0,
					b: 0,
					a: 1
				},
				rgba: {
					r: 100,
					g: 187,
					b: 227,
					a: 1
				}

			};
		},
		methods: {
			open(item) {
				this.$refs.colorPicker.open();
			},
			confirm(e) {
				this.rgba = e.rgba;
			}
		}
	};
</script>

<style>
	.t-page {}

	.button {
		display: flex;
		justify-content: center;
		align-items: center;
		margin: 30upx;
		height: 100upx;
		font-size: 32upx;
		color: #666;
		background: #42B983;
		border: 1px #eee solid;
		border-radius: 10upx;
		color: #fff;
	}
</style>
