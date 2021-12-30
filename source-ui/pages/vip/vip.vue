<template>
	<view>
		<view class="box">
			<view class="item-title" style="line-height: 50rpx;margin-top: -10rpx;">
				白银会员298元
			</view>
			<view class="item-content" style="color: red;line-height: 45rpx;">
				一年期限，线上牵线3个名额
			</view>
			<view class="item-desc" style="line-height: 42rpx;">
				选定目标，红娘线上牵线联系，以双方交换微信名片和真名为准。
				会员期内可享朋友圈推广，优先报名参加线下相亲活动等。
			</view>
		</view>
		<view class="box">
			<view class="item-title" style="line-height: 50rpx;margin-top: -10rpx;">
				钻石会员3688元
			</view>
			<view class="item-content" style="color: red;line-height: 45rpx;">
				两年期限，线下牵线3个名额
			</view>
			<view class="item-desc" style="line-height: 42rpx;">
				红娘跟你约谈后，以你的择偶要求，帮你深度了解会员，
				精准定位，帮你找，帮你约，陪你见，以双方约见为准。
				附赠线上牵线5次，365会员1年，可以优先报名参加线下活动，情感和个人形象指导。
			</view>
		</view>
		<view class="box">
			<view class="item-title" style="line-height: 50rpx;margin-top: -10rpx;">
				其他说明
			</view>
			<view class="item-desc" style="line-height: 42rpx;">
				<view>
					开通定制会员后，无其他额外费用。
				</view>
				<view>
					会员权益仅限本人，不可转增。
				</view>
				<view>
					会员权益有效期内领证结婚，权益立即失效。
				</view>
			</view>
		</view>
		<view class="box-button">
			<u-button shape="circle" type="error">联系红娘</u-button>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			}
		},
		methods: {
			
		}
	}
</script>

<style>
	page{
		background-color:#fdbcdb;
	}
</style>

<style lang="scss" scoped>
	.box {
		box-shadow: 0 2px 10px 0 rgba(0,0,0,.15);
		-webkit-box-shadow: 0 2px 10px 0 rgba(0,0,0,.15);
		-moz-box-shadow: 0 2px 10px 0 rgba(0,0,0,.15);
		-o-box-shadow: 0 2px 10px 0 rgba(0,0,0,.15);
		*border: 1px solid #d7d9e0;
		background-color: #FFFFFF;
		margin: 20rpx;
		border-radius: 10rpx;
		padding: 20rpx;
	}
	
	.box-button{
		border-radius: 20rpx;
		padding: 20rpx 20rpx;
		button{
			color: #FFFFFF;
			background-color: #feabd7;
		}
	}
</style>
