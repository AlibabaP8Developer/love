<template>
	<view>
		<view class="bg-title">个人中心</view>
		<view class="bg-main">
			<view class="u-flex user-box u-p-l-30 u-p-r-20 u-p-t-30 u-p-b-30">
				<view class="u-flex" @click="profile">
					<view class="u-m-r-20 ">
						<view class="main-flex avatar">
							<u-avatar :src="pic" size="140"></u-avatar>
						</view>
					</view>
					<view class="u-flex-1">
						<view class="u-font-18 u-p-b-20">詹Sir</view>
						<view class="u-font-12 tip" style="width: 320rpx;">
							去认证，解锁平台全部功能
							<u-icon name="arrow-right"></u-icon>
						</view>
					</view>
					<view class="u-flex-1">
						<view class="u-font-18 u-p-b-20">
							<view class="main-flex main-color main-bg-color qiandao">
								获得红线
							</view>
						</view>
					</view>
				</view>
			</view>
			<view class="u-font-12 tip update">编辑资料</view>
			<view class="center-nav">
				<u-row>
					<u-col span="2.2" text-align="center" v-for="(item,index) in navList1" :key="index">
						<view>
							<view class="tabNum">{{item.num}}</view>
							<view class="tabName">{{item.name}}</view>
						</view>
					</u-col>
				</u-row>
			</view>
			<view class="vip">
				<view>
					365会员
					<view class="item-line"></view>
					拥有专属权益
				</view>
				<view>
					<view class="main-flex main-color main-bg-color qiandao">
						了解详情
					</view>
				</view>
			</view>
		</view>
		<view class="navgraw">
			<view class="item-bottom" style="display: flex;align-items: center;padding-bottom: 20rpx;justify-content: space-between;">
				<view class="main-flex">
					<u-image  width="40rpx" height="40rpx" :src="ic_shiming"
					class="ic-img"></u-image>
					<text class="u-p-l-20">认证</text>
				</view>
				<view class="section-right">
					赠红线
					<u-icon name="arrow-right"></u-icon>
				</view>
			</view>
			<view class="center-nav">
				<u-row>
					<u-col span="2.4" v-for="(item,index) in navList2" :key="index">
						<view style="display: flex;flex-direction: column;justify-content: center;align-items: center;">
							<view style="background-color: #d9d9d9;width: 80rpx;height: 80rpx;border-radius: 100%;" class="main-flex">
								<image :src="item.pic" mode="widthFix"
								style="background-color: #d9d9d9;width: 50rpx;"></image>
							</view>
							<view class="tabName item-desc">{{item.name}}</view>
						</view>
					</u-col>
				</u-row>
			</view>
		</view>
		<view class="navCell">
			<view class="section">
				<view class="section-title">
					<u-image width="40rpx" height="40rpx" :src="ic_collect"
					></u-image>
					<text class="u-m-l-20 u-font-14">我的收藏</text>
				</view>
				<view class="section-right">
					<u-icon name="arrow-right"></u-icon>
				</view>
			</view>
			<view class="section">
				<view class="section-title">
					<u-image width="40rpx" height="40rpx" :src="ic_dynamic"
					></u-image>
					<text class="u-m-l-20 u-font-14">我的动态</text>
				</view>
				<view class="section-right">
					<u-icon name="arrow-right"></u-icon>
				</view>
			</view>
			
			<view class="section">
				<view class="section-title">
					<u-image width="40rpx" height="40rpx" :src="ic_peach"
					></u-image>
					<text class="u-m-l-20 u-font-14">福利中心</text>
				</view>
				<view class="section-right">
					<u-icon name="arrow-right"></u-icon>
				</view>
			</view>
			
			<view class="section">
				<view class="section-title">
					<u-image width="40rpx" height="40rpx" :src="ic_kefu"
					></u-image>
					<text class="u-m-l-20 u-font-14">联系客服</text>
				</view>
				<view class="section-right">
					<u-icon name="arrow-right"></u-icon>
				</view>
			</view>
			
			<view class="section">
				<view class="section-title">
					<u-image width="40rpx" height="40rpx" :src="ic_vip"
					></u-image>
					<text class="u-m-l-20 u-font-14">公众号</text>
				</view>
				<view class="section-right">
					<u-icon name="arrow-right"></u-icon>
				</view>
			</view>
			
			<view class="section">
				<view class="section-title">
					<u-image width="40rpx" height="40rpx" :src="ic_shezhi"
					></u-image>
					<text class="u-m-l-20 u-font-14">设置</text>
				</view>
				<view class="section-right">
					<u-icon name="arrow-right"></u-icon>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				pic:'http://8.136.213.245/profile/avatar/2021/04/27/2c7c5a9c6934323f5247c6fd4c0bdbc4.png',
				show:true,
				ic_shiming:'https://api.citymiai.com/media/common/images/ic_shiming.png',
				navList1:[
				   {name:"红线",num:"0"},
				   {name:"桃花",num:"20"},
				   {name:"谁看过我",num:"9"},
				   {name:"谁收藏我",num:"1"},
				   {name:"资料完成",num:"79%"}
				],
				navList2:[
				   {name:"身份",pic:"https://api.citymiai.com/media/common/images/identify_icon_name.png"},
				   {name:"学历",pic:"https://api.citymiai.com/media/common/images/identify_icon_education.png"},
				   {name:"工作",pic:"https://api.citymiai.com/media/common/images/identify_icon_work.png"},
				   {name:"车产",pic:"https://api.citymiai.com/media/common/images/identify_icon_house.png"},
				   {name:"房产",pic:"https://api.citymiai.com/media/common/images/identify_icon_car.png"}
				],
				ic_collect:'https://api.citymiai.com/media/common/images/ic_collect.png',
				ic_dynamic:'https://api.citymiai.com/media/common/images/ic_dynamic.png',
				ic_peach:'https://api.citymiai.com/media/common/images/ic_peach.png',
				ic_shezhi:'https://api.citymiai.com/media/common/images/ic_shezhi.png',
				ic_right:'https://api.citymiai.com/media/common/images/ic_right.png',
				ic_kefu:'https://api.citymiai.com/media/common/images/ic_kefu.png',
				ic_vip:'https://api.citymiai.com/media/common/images/ic_vip.png',
			}
		},
		onLoad() {
			
		},
		methods: {
			logout() {
				// 登录成功修改token与用户信息
				this.$u.vuex('vuex_token', '');
				this.$u.vuex('vuex_user', {});
				this.$u.route('/pages/login/login')
			},
			profile(){
				this.$u.route('/pages/profile/profile')
			},
			setting(){
				this.$u.route('/pages/profile/setting')
			},
			scan(){
				console.log('begin scan');
				// 允许从相机和相册扫码
				uni.scanCode({
				    success: function (res) {
				        console.log('条码类型：' + res.scanType);
				        console.log('条码内容：' + res.result);
				    }
				});
			},
			//拨打固定电话
			callPhoneNumber() {
				uni.makePhoneCall({
					phoneNumber: "18720989281",
				});
			},
			problem(){
				this.$u.route({
					url: 'pages/login/problem'
				})
			},
			// 关于作者
			aboutMe() {
				uni.navigateTo({
					url: '../me/aboutMe'
				})
			},
			clickNav(){
				uni.makePhoneCall({
					phoneNumber: "18720989281",
				});
			}
		}
	}
</script>

<style lang="scss">
.bg-title{
	background-color: #fe3ea5;
	text-align: center;
	color: #FFFFFF;
	font-size: 15px;
	height: 40px;
	line-height: 40px;
	font-weight: bold;
}
.bg-main{
	background-color: #fe3ea5;
	background:linear-gradient(to bottom,#fe3ea5,#ee7e59);
	height: 450rpx;
	color: #FFFFFF;
	border-radius: 0 0 30px 30px;
	.avatar{
		width: 148rpx;height: 148rpx;background-color: #FFFFFF;border-radius: 100%;
	}
	.qiandao{
		width: 200rpx;
		border-radius: 30%;
		font-size: 14px;
		margin-left: 10rpx;
		padding: 5rpx 0;
	}
	.tip{
		color: #eaeaea;
	}
	.update{
		margin-left: 50rpx;
		margin-top: -20rpx;
	}
	.center-nav{
		margin-top: 20rpx;
		margin-left: 20rpx;
	}
	.vip{
		margin: 30rpx;
		padding: 30rpx;
		background-color: #344072;
		border-radius: 20rpx 20rpx 20rpx 20rpx;
		display: flex;
		justify-content: space-between;
	}
}

.navgraw{
	background-color: #ffffff;
	border-radius: 10px;
	margin: 20rpx 30rpx 30rpx 30rpx;
	padding: 20rpx 30rpx 0 20rpx;
	.section-right{
		font-size: 28rpx;color: #909399;
	}
}

.navCell{
	background-color: #ffffff;
	border-radius: 10px;
	margin: -10rpx 30rpx 30rpx 30rpx;
	padding: 0 30rpx 0 30rpx;
	.section{
		padding-top: 20rpx;
		border-bottom: 1px solid #ecf1fa;
		padding-bottom: 20rpx;
		display: flex;justify-content: space-between;
		.section-title{
			font-size: 32rpx;color: #303133;display: flex;justify-content:center;align-items: center;
		}
		.section-right{
			font-size: 28rpx;color: #909399;
		}
	}
}

</style>