<template>
	<view @longpress="onLong">
		<!-- 时间显示 -->
		<view class=" flex align-center justify-center py-1">
			<text class="font-sm text-light-muted">{{showTime}}</text>
		</view>
		<!-- 聊天气泡 -->
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
	import $T from '@/common/time.js'
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
			},
			preTime: {
				tyepe: [String, Number],
				default: 0
			},
			index: Number,
		},
		computed: {
			//是否是本人
			isSelf() {
				//id为1是本人
				const id = 1;
				return this.item.user_id === id
			},
			showTime() {
				return $T.getChatTime(this.item.create_time, this.preTime)
			}
		},
		methods: {
			onLong(e) {
				// console.log(e)
				let x = 0;
				let y = 0;
				if (Array.isArray(e.changedTouches) && e.changedTouches.length > 0) {
					//微信小程序是client,h5是screen
					x = e.changedTouches[0].clientX || e.changedTouches[0].screenX;
					y = e.changedTouches[0].clientY || e.changedTouches[0].screenY;
				}
				this.$emit('Long', {
					x,
					y,
					index: this.index,
				});
				// console.log(x, y)
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