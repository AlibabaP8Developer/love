<template>
	<view class="u-m-t-20">
		<view class="u-p-t-30 u-p-b-30 section">
			<view class="main-flex">
				<u-image width="100rpx" height="100rpx" :src="ic_message"
				class="u-m-l-60"></u-image>
				<view class="u-m-l-20">
					<view class="item-title">
						消息订阅
					</view>
					<view class="item-desc">
						关闭后将错过不少缘分
					</view>	
				</view>
			</view>
			<u-icon name="arrow-right" class="section-right"></u-icon>
		</view>
		<view class="u-p-t-30 u-p-b-30 section">
			<view class="main-flex">
				<u-image width="100rpx" height="100rpx" :src="ic_friend"
				class="u-m-l-60"></u-image>
				<view class="u-m-l-20">
					<view class="item-title">
						联系过的人
					</view>
					<view class="item-desc">
						去看看哪些人联系过了
					</view>	
				</view>
			</view>
			<u-icon name="arrow-right" class="section-right"></u-icon>
		</view>
		<view class="u-p-t-30 u-p-b-30 section">
			<view class="main-flex">
				<u-image width="100rpx" height="100rpx" :src="ic_xitong"
				class="u-m-l-60"></u-image>
				<view class="u-m-l-20">
					<view class="item-title">
						系统消息
					</view>
					<view class="item-desc">
						查看官方消息
					</view>	
				</view>
			</view>
			<u-icon name="arrow-right" class="section-right"></u-icon>
		</view>
		<view class="main-flex u-m-t-80">
			<u-image width="300rpx" height="300rpx" :src="no_message"></u-image>
		</view>
		<view class="item-desc u-text-center">暂无消息</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				ic_message:'https://api.citymiai.com/media/common/images/ic_message.png',
				ic_friend:'https://api.citymiai.com/media/common/images/ic_friend.png',
				ic_xitong:'https://api.citymiai.com/media/common/images/ic_xitong.png',
				no_message:'https://api.citymiai.com/media/common/images/no_message.png'
			}
		},
		methods: {
			
		}
	}
</script>

<style>
	.section{
		 background-color: #FFFFFF;
		 border-bottom: 1px solid #ecf1fa;
		 display: flex;justify-content: space-between;
		.section-title{
			font-size: 32rpx;color: #303133;display: 
			flex;justify-content:center;align-items: center;
		}
	}
	
	.section-right{
		font-size: 28rpx;
		color: #909399;
		margin-right: 20rpx;
	}
</style>
