<template>
	<!-- 弹出层 -->
	<view class="" style="z-index: 9999; overflow: hidden;" v-show="status">
		<!-- 遮罩层 -->
		<view v-if="mask" @click="hide" class="position-fixed top-0 right-0 left-0 bottom-0" :style="getMaskColor">
		</view>
		<view class="position-fixed bg-white" :class="getBodyClass" :style="getBodyStyle">
			<slot></slot>
		</view>
	</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				x: -1,
				y: -1,
				status: false
			}
		},
		methods: {
			show(x = 0, y = 0) {
				this.x = x;
				this.y = y;
				this.status = true;
			},
			hide() {
				this.status = false;
			}
		},
		props: {
			//遮罩层颜色
			maskColor: {
				type: Boolean,
				default: false,
			},
			//是否开启遮罩
			mask: {
				type: Boolean,
				default: true
			},
			//是否处于底部
			fixBottom: {
				type: Boolean,
				default: false
			}
		},
		computed: {
			getMaskColor() {
				let color = this.maskColor ? 0.5 : 0;
				return `background-color:rgba(0,0,0,${color})`;
			},
			getBodyClass() {
				let fixBottom = this.fixBottom ? 'left-0 right-0 bottom-0' : 'rounded border';
				return fixBottom;
			},

			getBodyStyle() {
				let left = this.x > -1 ? `left:${this.x}px;` : '';
				let top = this.y > -1 ? `top:${this.y}px;` : '';
				// return 'left:20rpx;bottom:20rpx;right:20rpx;'
				return `${left}${top}`;
			}
		}
	}
</script>

<style>

</style>