<template>
	<view>
		<!-- 左边好友栏 -->
		<view v-if="!isSelf" class="flex pl-2 pt-2 mb-1" style="position: relative;">
			<MyAvatar :src="item.avatar" size="70">
			</MyAvatar>
			<text class="chat-left-icon iconfont font-md text-white position-absolute">&#xe609;</text>
			<view class="bg-white rounded pd ml-3" style="max-width: 500rpx;">
				<text class="font-md">{{item.data}}</text>
			</view>
		</view>
		<!-- 右边用户栏 -->
		<view v-else class="flex pr-2 pt-2 mb-1 align-start justify-end position-relative" style="">
			<view class="bg-chat-item rounded pd mr-3" style="max-width: 500rpx;">
				<text class="font-md">{{item.data}}</text>
			</view>
			<text class="chat-right-icon iconfont font-md text-chat-item position-absolute">&#xe640;</text>
			<MyAvatar :src="item.avatar" size="70">
			</MyAvatar>
		</view>
	</view>

</template>

<script>
	import MyAvatar from '@/compoents/my-ui/my-avatar.vue'
	export default {
		components: {
			MyAvatar
		},
		data() {
			return {}
		},

		props: {
			item: {
				type: Object,
				default: ''
			}
		},
		computed: {
			//是否是本人
			isSelf() {
				//id为1是本人
				const id = 1;
				return this.item.user_id === id
			}
		}
	}
</script>
<style scoped>
	.chat-left-icon {
		left: 95rpx;
		top: 40rpx;
	}

	.chat-right-icon {
		right: 95rpx;
		top: 40rpx;
	}

	.pd {
		padding: 15rpx;
	}
</style>