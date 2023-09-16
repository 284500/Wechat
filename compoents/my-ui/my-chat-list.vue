<template>
	<view class="flex align-center;">
		<!-- 头像 -->
		<view class="flex align-center justify-center position-relative" style="width: 145rpx;height: 135rpx;">
			<my-avatar :src="item.avater"></my-avatar>
			<!-- 消息角标 -->
			<my-badge badge-class="position-absolute" badge-style="right:15rpx;top:14rpx">{{index+1}}</my-badge>
		</view>
		<!-- 信息栏 -->
		<view class="flex flex-column border-bottom flex-1 py-3 pr-3 border-light-secondary">
			<view class="flex justify-between align-center mb-1">
				<text class="font-md">{{item.nickname}}</text>
				<text class="font-sm text-light-muted">{{item.update_time | formatTime}}</text>
			</view>
			<text class="font text-ellipsis text-light-muted">{{item.data}}</text>
		</view>
	</view>
</template>

<script>
	import MyAvatar from '@/compoents/my-ui/my-avatar.vue'
	import MyBadge from '@/compoents/my-ui/my-badge.vue'
	import $Time from '@/common/time.js'
	export default {
		components: {
			MyAvatar,
			MyBadge
		},
		data() {
			return {

			}
		},
		props: {
			item: Object,
			index: Number,
		},
		filters: {
			formatTime(value) {
				return $Time.gettime(value)
			}
		}
	}
</script>

<style>

</style>