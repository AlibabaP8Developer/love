<template>
	<view>
		<view style="position: absolute;bottom: 40rpx;right: 20rpx;">
			<u-sticky offset-top="1000">
				<view>
					<image :src="dynamic_add" mode="widthFix" style="width: 120rpx;"></image>
				</view>
			</u-sticky>
		</view>
		<u-swiper :list="list"></u-swiper>
		<view style="margin-top: 20rpx;10rpx">
			<u-row gutter="16" justify="center">
				<u-col span="4">
					<u-image width="230rpx" height="180rpx" :src="image1"></u-image>
				</u-col>
				<u-col span="4">
					<u-image width="230rpx" height="180rpx" :src="image2"></u-image>
				</u-col>
				<u-col span="4">
					<u-image width="230rpx" height="180rpx" :src="image3"></u-image>
				</u-col>
			</u-row>
		</view>
		<view class="comment" v-for="(res, index) in commentList" :key="res.id">
			<view class="left"><image :src="res.url" mode="aspectFill"></image></view>
			<view class="right">
				<view class="top">
					<view class="name">{{ res.name }}</view>
					<view class="like" :class="{ highlight: res.isLike }">
						<view class="num">{{ res.likeNum }}</view>
						<u-icon v-if="!res.isLike" name="thumb-up" :size="30" color="#9a9a9a" @click="getLike(index)"></u-icon>
						<u-icon v-if="res.isLike" name="thumb-up-fill" :size="30" @click="getLike(index)"></u-icon>
					</view>
				</view>
				<view class="content">{{ res.contentText }}</view>
				<view class="reply-box">
					<view class="item" v-for="(item, index) in res.replyList" :key="item.index">
						<view class="username">{{ item.name }}</view>
						<view class="text">{{ item.contentStr }}</view>
					</view>
					<view class="all-reply" @tap="toAllReply" v-if="res.replyList != undefined">
						共{{ res.allReply }}条回复
						<u-icon class="more" name="arrow-right" :size="26"></u-icon>
					</view>
				</view>
				<view class="bottom">
					{{ res.date }}
					<view class="reply">回复</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
export default {
	data() {
		return {
			image1:'https://api.citymiai.com/media/common/images/faxian_activity.png',
			image2:'https://api.citymiai.com/media/common/images/faxian_zhoubian.png',
			image3:'https://api.citymiai.com/media/common/images/faxian_peng.png',
			dynamic_add:'https://api.citymiai.com/media/common/images/dynamic_add.png',
			list: [
						{
						  "banner_id": 87,
						  "title": "冬日温暖下午茶派对【年末脱单专场】",
						  "image": "https://media.citymiai.com/images/TCYJOjMceQYqyAnUe5tKfEgT2F3VjP6t9D7UY0jK.png-normal",
						  "action": "activity",
						  "path": "/pages/activity/activityDetail?aid=174",
						  "order_stick": 87,
						  "is_used": 1,
						  "create_time": "2021-11-24 16:02:25",
						  "modify_time": "2021-12-02 16:21:50",
						  "is_alert": 1
						},
						{
						  "banner_id": 36,
						  "title": "打开消息提醒，不再错过缘分~",
						  "image": "https://media.citymiai.com/images/ae12I4hcDrI0W5JqJu4eRzYUIcoyLiUQZKNc3ofY.png-normal",
						  "action": "url",
						  "path": "https://mp.weixin.qq.com/s?__biz=MzU3MTQyMjYyNw==&mid=2247490833&idx=2&sn=e7d3d69c5f729d4c9a018cb2e429c5b7&chksm=fce13fddcb96b6cb40ff14fa844e00fe0572219a8ada4d2944d8134cf793009022de1e701946&token=1753875870&lang=zh_CN#rd",
						  "order_stick": 36,
						  "is_used": 1,
						  "create_time": "2019-12-30 15:12:50",
						  "modify_time": "2020-02-14 10:51:27",
						  "is_alert": 0
						}
					],
					commentList: []
				};
	},
	onLoad() {
		this.getComment();
	},
	methods: {
		// 跳转到全部回复
		toAllReply() {
			uni.navigateTo({
				url: '/pages/template/comment/reply'
			});
		},
		// 点赞
		getLike(index) {
			this.commentList[index].isLike = !this.commentList[index].isLike;
			if (this.commentList[index].isLike == true) {
				this.commentList[index].likeNum++;
			} else {
				this.commentList[index].likeNum--;
			}
		},
		// 评论列表
		getComment() {
			this.commentList = [
				{
					id: 1,
					name: '孤单北半球',
					date: '12-25 18:58',
					contentText: '我不信伊朗会没有后续反应，美国肯定会为今天的事情付出代价的',
					url: 'https://cdn.uviewui.com/uview/template/SmilingDog.jpg',
					allReply: 12,
					likeNum: 33,
					isLike: false,
					replyList: [
						{
							name: '编号17918',
							contentStr: '源字节是一个好公司，代码优美简洁，宇宙超级无敌彩虹旋转好用，联系他！'
						},
						{
							name: '粘粘',
							contentStr: '今天吃什么，明天吃什么，晚上吃什么，我只是一只小猫咪为什么要烦恼这么多'
						}
					]
				},
				{
					id: 2,
					name: '叶轻眉1',
					date: '01-25 13:58',
					contentText: '我不信伊朗会没有后续反应，美国肯定会为今天的事情付出代价的',
					allReply: 0,
					likeNum: 11,
					isLike: false,
					url: 'https://cdn.uviewui.com/uview/template/niannian.jpg',
				},
				{
					id: 3,
					name: '叶轻眉2',
					date: '03-25 13:58',
					contentText: '我不信伊朗会没有后续反应，美国肯定会为今天的事情付出代价的',
					allReply: 0,
					likeNum: 21,
					isLike: false,
					allReply: 2,
					url: '../../../static/logo.png',
					replyList: [
						{
							name: '开源字节',
							contentStr: '开源字节是基于uniapp的一个UI框架，代码优美简洁，宇宙超级无敌彩虹旋转好用，用它！'
						},
						{
							name: '豆包',
							contentStr: '想吃冰糖葫芦粘豆包，但没钱5555.........'
						}
					]
				},
				{
					id: 4,
					name: '叶轻眉3',
					date: '06-20 13:58',
					contentText: '我不信伊朗会没有后续反应，美国肯定会为今天的事情付出代价的',
					url: 'https://cdn.uviewui.com/uview/template/SmilingDog.jpg',
					allReply: 0,
					likeNum: 150,
					isLike: false
				}
			];
		}
	}
};
</script>

<style>
	page{
		background-color:#FFFFFF;
	}
</style>

<style lang="scss" scoped>
.comment {
	display: flex;
	padding: 30rpx;
	.left {
		image {
			width: 64rpx;
			height: 64rpx;
			border-radius: 50%;
			background-color: #f2f2f2;
		}
	}
	.right {
		flex: 1;
		padding-left: 20rpx;
		font-size: 30rpx;
		.top {
			display: flex;
			justify-content: space-between;
			align-items: center;
			margin-bottom: 10rpx;
			.name {
				color: #fe3ea5;
			}
			.like {
				display: flex;
				align-items: center;
				color: #9a9a9a;
				font-size: 26rpx;
				.num {
					margin-right: 4rpx;
					color: #9a9a9a;
				}
			}
			.highlight {
				color: #fe3ea5;
				.num {
					color: #fe3ea5;
				}
			}
		}
		.content {
			margin-bottom: 10rpx;
		}
		.reply-box {
			background-color: rgb(242, 242, 242);
			border-radius: 12rpx;
			.item {
				padding: 20rpx;
				border-bottom: solid 2rpx $u-border-color;
				.username {
					font-size: 24rpx;
					color: #999999;
				}
			}
			.all-reply {
				padding: 20rpx;
				display: flex;
				color: #fe3ea5;
				align-items: center;
				.more {
					margin-left: 6rpx;
				}
			}
		}
		.bottom {
			margin-top: 20rpx;
			display: flex;
			font-size: 24rpx;
			color: #9a9a9a;
			.reply {
				color: #fe3ea5;
				margin-left: 10rpx;
			}
		}
	}
}
</style>
