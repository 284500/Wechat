<template>
	<view>
		<view class="bg-light" :class="fixed?'fixed-top':'fixed'">
			<!-- 状态栏 -->
			<view class="" :style="'height:'+statusBarHeight+'px'"></view>
			<!-- 导航栏 -->
			<view class="w-100 flex justify-between align-center border" style="height: 90rpx;">
				<!-- 左边 -->
				<view class="">
					<solt>
						<text v-if="title" class="font-md ml-3">{{title}}
						</text>
					</solt>
					<!-- <text class="iconfont">&#xe719;</text> -->
				</view>
				<!-- 右边 -->
				<view class="flex align-center">
					<my-icon-button :icon="'\ue693'" @click="a"></my-icon-button>
					<my-icon-button :icon="'\ue628'"></my-icon-button>
				</view>
			</view>
		</view>
		<!-- 占位 -->
		<view v-if="fixed" :style="fixedStyle">
		</view>
	</view>
</template>

<script>
	import MyIconButton from '@/compoents/my-ui/my-icon-button.vue'
	export default {
		components: {
			MyIconButton
		},
		props: {
			title: {
				type: [String, Boolean],
				default: false
			},
			fixed: {
				type: Boolean,
				default: true
			}
		},
		data() {
			return {
				statusBarHeight: 0,
				navBarHeight: 0
			}
		},
		onLoad() {

		},
		methods: {

		},
		computed: {
			fixedStyle() {
				return `height:${this.navBarHeight}px`
			}
		},
		mounted() {
			// #ifdef APP-PLUS-NVUE
			this.statusBarHeight = plus.navigator.getStatusbarHeight();
			//#endif
			this.navBarHeight = this.statusBarHeight + uni.upx2px(90);
		}
	}
</script>

<style>
</style>