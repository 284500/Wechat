<template>
	<!-- 弹出层 -->
	<view class="" style="z-index: 9999; overflow: hidden;" v-show="status">
		<!-- 遮罩层 -->
		<view @click="hide" class="position-fixed top-0 right-0 left-0 bottom-0"
			style="background-color: rgba(0,0,0,0.5);">
		</view>
		<view class="position-fixed bg-white" :style="popStyle">
			<slot></slot>
		</view>
	</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				status: false
			}
		},
		methods: {
			show() {
				this.status = true;
			},
			hide() {
				this.status = false;
			}
		},
		props: {
			popStyle: {
				type: String,
				default: "",
			}
		}
	}
</script>

<style>

</style>