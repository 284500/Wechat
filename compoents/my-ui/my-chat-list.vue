<template>
	<view class="flex align-center;" hover-class="bg-hover-light" @click="onClick" @longpress="onLong">
		<!-- 头像 -->
		<view class="flex align-center justify-center position-relative" style="width: 145rpx;height: 135rpx;">
			<my-avatar :src="item.avater"></my-avatar>
			<!-- 消息角标 -->
			<my-badge v-if="item.num>0" badge-class="position-absolute"
				badge-style="right:15rpx;top:14rpx">{{item.num ||index+1}}</my-badge>
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
	import mixin from '@/common/mixin/base.js'
	export default {
		components: {
			MyAvatar,
			MyBadge
		},
		mixins: [mixin],
		data() {
			return {

			}
		},
		methods: {
			onClick() {
				this.$emit('click');
				console.log("ada")
			},
			onLong(e) {
				console.log(e)
			}
		},
		props: {
			item: Object,
			index: Number,
		},

	}
</script>

<style>

</style>