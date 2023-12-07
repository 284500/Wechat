<template>
	<view class="bg-white flex align-stretch" hover-class="bg-light" @click="$emit('click')">
		<view class="flex align-center justify-between py-2 px-3">
			<img v-if="imgUrl" :src="imgUrl" mode="withFix" style="width: 75rpx;height: 75rpx;">
		</view>
		<view class="flex-1 border-bottom flex align-center">
			<text class="font-md text-dark">{{title}}</text>
		</view>
	</view>
</template>

<script>
	export default {
		props: {
			imgUrl: {
				type: String,
				default: ''
			},
			title: {
				type: String,
				default: ''
			}
		}
	}
</script>

<style>
</style>