<template>
	<view class="u-p-l-20 u-p-r-20 u-p-t-20">
		<view class="main-flex">
			<u-search placeholder="搜索会员" input-align="left"  :show-action="false" :clearabled="true" :disabled="true" style="width: 690rpx;" @click="search"></u-search>
			<view @click="code" class="main-flex main-color u-p-l-20">
				<view class="main-flex main-bold-color main-bg-color qiandao">
					签到
				</view>
			</view>
		</view>
		<view class="u-p-t-30 u-p-b-30">
			<u-section title="最新上墙" sub-title="全部" :show-line="false" :bold="false" font-size="32"></u-section>
		</view>
		<view>
			<view class="skill-sequence-panel-content-wrapper">
				<scroll-view scroll-x="true" class="kite-classify-scroll">
					<view class="kite-classify-cell">
						<image src="../../static/img/index/ic_wall_add.png" class="wall-add"></image>
						<view class="u-main-color">我要上墙</view>
					</view>
					<view class="kite-classify-cell" v-for="(item, index) in curriculum" :key="index">
						<view class="main-flex cell-view">
							<view class="main-flex cell-img">
								<image :src="item.src"></image>
							</view>
						</view>
						<view class="u-main-color">{{item.code}}</view>
					</view>
				</scroll-view>
			</view>
		</view>
		<view class="u-p-t-50 u-p-b-30">
			<view class="section">
				<view class="section-title">
					推荐单身
					<u-image width="32rpx" height="32rpx" :src="ic_liebiao"
					class="u-m-l-60"></u-image>
				</view>
				<view class="section-right">
					最新
					<u-icon name="arrow-right"></u-icon>
				</view>
			</view>
		</view>
		<view>
			<view v-for="(item, index) in flowList" :key="index">
			    <u-lazy-load :image="item.base_zhaopian" img-mode="aspectFill"
				height="500"></u-lazy-load>
			    <view class="item-title">
					编号:{{item.uid}}
					<u-image v-if="item.base_xingbie === 2" width="30rpx" height="30rpx" :src="label_woman" class="ic-img"></u-image>
					<u-image v-else-if="item.base_xingbie === 1" width="30rpx" height="30rpx" :src="label_man" class="ic-img"></u-image>
					<u-image v-if="item.shiming_ispass === 2" width="30rpx" height="30rpx" :src="label_shiming"
					class="ic-img"></u-image>
				</view>
				<view class="item-content">{{item.base_nianling}}岁
				<view class="item-line"></view>{{item.base_shuxiang}}
				<view class="item-line"></view>{{item.base_shengao}}cm
				<view class="item-line"></view>{{item.work_xueli}}
				<view class="item-line"></view>{{item.work_nianxin}}</view>
			    <view class="item-desc item-bottom">{{item.work_danwei}}
				<view class="item-line"></view>{{item.work_hangye}}
				<view class="item-line"></view>{{item.base_hunshi}}</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				ic_liebiao:'https://api.citymiai.com/media/common/images/ic_liebiao.png',
				ic_block:'https://api.citymiai.com/media/common/images/ic_block.png',
				label_woman:'https://api.citymiai.com/media/common/images/label_woman.png',
				label_man:'https://api.citymiai.com/media/common/images/label_man.png',
				label_shiming:'https://api.citymiai.com/media/common/images/label_shiming.png',
				curriculum: [
					{
						code: '编号:16155',
						src: 'https://media.citymiai.com/images/BEenwbzr6MgLsDyZNieiAb1rhRqaKH6cPFpdBrAA.png-avatar200'
					},
					{
						code: '编号:17406',
						src: 'https://media.citymiai.com/shaoxing/album/ZOwQiJC0htbqZHczn1124rFx0LxBjOAXMdZdvehR.png-avatar200'
					},
					{
						code: '编号:18015',
						src: 'https://media.citymiai.com/images/M1KfGxE3bXFuXXszOOXYha0CGznHSagEQqi0ipKo.png-avatar200'
					},
					{
						code: '编号:15909',
						src: 'https://media.citymiai.com/shaoxing/album/gGACd5FpOjwU3vVxkzpnVgOg0qDV9gfr0rzDfIjj.png-avatar200'
					}
				],
				flowList: [],
			}
		},
		onLoad() {
			uni.$on('findIndexHouseList', (obj) => {
				// 获取数据
				this.findHouseList(1);
			})
			// 获取数据
			this.findHouseList();
		},
		onUnload() {
			// 移除监听事件  
			uni.$off('findIndexHouseList');
		},
		onPageScroll(e) {
		    this.scrollTop = e.scrollTop;
		},
		onReachBottom() {
		    this.loadStatus = 'loading';
		    // 获取数据
			this.findHouseList()
		},
		// 下拉刷新
		onPullDownRefresh() {
			// 获取数据
			this.findHouseList(1);
			// 关闭刷新
			uni.stopPullDownRefresh();
		},
		methods: {
			findHouseList(type = 0) {
				this.flowList = [
    {
      "uid": 12116,
      "base_zhaopian": "https://media.citymiai.com/shaoxing/album/gGACd5FpOjwU3vVxkzpnVgOg0qDV9gfr0rzDfIjj.png-normal",
      "base_zhaopian_thum": "https://media.citymiai.com/shaoxing/album/gGACd5FpOjwU3vVxkzpnVgOg0qDV9gfr0rzDfIjj.png-avatar200",
      "base_xingbie": 2,
      "is_cert": 0,
      "shiming_ispass": 2,
      "base_shengri": "1996-04-27",
      "base_shuxiang": "鼠",
      "base_shengao": "158",
      "work_xueli": "本科",
      "work_nianxin": "6万-8万",
      "work_danwei": "私企",
      "work_hangye": "广告/传媒/出版",
      "base_hunshi": "未婚",
      "is_collect": false,
      "base_nianling": 25,
      "vip": null,
      "svip": null
    },
    {
      "uid": 16315,
      "base_zhaopian": "https://media.citymiai.com/shaoxing/album/0h7rYXYJumRzMOXUQSj86CMldaCcv6FMyfVh3lRc.png-normal",
      "base_zhaopian_thum": "https://media.citymiai.com/shaoxing/album/0h7rYXYJumRzMOXUQSj86CMldaCcv6FMyfVh3lRc.png-avatar200",
      "base_xingbie": 1,
      "is_cert": 0,
      "shiming_ispass": 2,
      "base_shengri": "1995-01-09",
      "base_shuxiang": "猪",
      "base_shengao": "176",
      "work_xueli": "大专",
      "work_nianxin": "15万-20万",
      "work_danwei": "事业单位",
      "work_hangye": "其他",
      "base_hunshi": "未婚",
      "is_collect": false,
      "base_nianling": 26,
      "vip": {
        "vip_id": 328,
        "uid": 16315,
        "count_tuijian": 0,
        "count_wechat": 1,
        "count_toutiao": 1,
        "count_activity": 3,
        "end_time": "2022-12-03 01:47:37",
        "create_time": "2021-12-03 01:47:37",
        "update_time": "2021-12-03 01:47:37",
        "is_vip": 1,
        "count_friends": 0,
        "count_groups": 0,
        "vip_type": "Vip365"
      },
      "svip": null
    },
    {
      "uid": 14275,
      "base_zhaopian": "https://media.citymiai.com/shaoxing/album/ZOwQiJC0htbqZHczn1124rFx0LxBjOAXMdZdvehR.png-normal",
      "base_zhaopian_thum": "https://media.citymiai.com/shaoxing/album/ZOwQiJC0htbqZHczn1124rFx0LxBjOAXMdZdvehR.png-avatar200",
      "base_xingbie": 2,
      "is_cert": 0,
      "shiming_ispass": 2,
      "base_shengri": "1993-08-27",
      "base_shuxiang": "鸡",
      "base_shengao": "160",
      "work_xueli": "大专",
      "work_nianxin": "6万-8万",
      "work_danwei": "私企",
      "work_hangye": "教育/培训/科研",
      "base_hunshi": "离异",
      "is_collect": false,
      "base_nianling": 28,
      "vip": {
        "vip_id": 131,
        "uid": 14275,
        "count_tuijian": 0,
        "count_wechat": 1,
        "count_toutiao": 1,
        "count_activity": 3,
        "end_time": "2022-12-02 22:26:24",
        "create_time": "2020-09-13 20:48:31",
        "update_time": "2021-12-02 22:26:24",
        "is_vip": 1,
        "count_friends": 0,
        "count_groups": 0,
        "vip_type": "Vip365"
      },
      "svip": null
    },
    {
      "uid": 12771,
      "base_zhaopian": "https://media.citymiai.com/shaoxing/album/hxEYNUL7PIVAuS1FCF66MwZWjsYIhxZwX0A8y8wy.png-normal",
      "base_zhaopian_thum": "https://media.citymiai.com/shaoxing/album/hxEYNUL7PIVAuS1FCF66MwZWjsYIhxZwX0A8y8wy.png-avatar200",
      "base_xingbie": 1,
      "is_cert": 0,
      "shiming_ispass": 2,
      "base_shengri": "1993-10-10",
      "base_shuxiang": "鸡",
      "base_shengao": "178",
      "work_xueli": "大专",
      "work_nianxin": "20万-50万",
      "work_danwei": "自有公司",
      "work_hangye": "汽车/交通/运输",
      "base_hunshi": "未婚",
      "is_collect": false,
      "base_nianling": 28,
      "vip": null,
      "svip": null
    },
    {
      "uid": 10245,
      "base_zhaopian": "https://media.citymiai.com/images/BEenwbzr6MgLsDyZNieiAb1rhRqaKH6cPFpdBrAA.png-normal",
      "base_zhaopian_thum": "https://media.citymiai.com/images/BEenwbzr6MgLsDyZNieiAb1rhRqaKH6cPFpdBrAA.png-avatar200",
      "base_xingbie": 1,
      "is_cert": 0,
      "shiming_ispass": 2,
      "base_shengri": "1994-12-18",
      "base_shuxiang": "狗",
      "base_shengao": "175",
      "work_xueli": "本科",
      "work_nianxin": "10万-15万",
      "work_danwei": "事业单位",
      "work_hangye": "其他",
      "base_hunshi": "未婚",
      "is_collect": false,
      "base_nianling": 26,
      "vip": null,
      "svip": null
    },
    {
      "uid": 13970,
      "base_zhaopian": "https://media.citymiai.com/images/M1KfGxE3bXFuXXszOOXYha0CGznHSagEQqi0ipKo.png-normal",
      "base_zhaopian_thum": "https://media.citymiai.com/images/M1KfGxE3bXFuXXszOOXYha0CGznHSagEQqi0ipKo.png-avatar200",
      "base_xingbie": 1,
      "is_cert": 0,
      "shiming_ispass": 0,
      "base_shengri": "1992-09-12",
      "base_shuxiang": "猴",
      "base_shengao": "178",
      "work_xueli": "本科",
      "work_nianxin": "15万-20万",
      "work_danwei": "私企",
      "work_hangye": "医疗/健康",
      "base_hunshi": "未婚",
      "is_collect": false,
      "base_nianling": 29,
      "vip": null,
      "svip": null
    },
    {
      "uid": 15756,
      "base_zhaopian": "https://media.citymiai.com/shaoxing/album/4pLvfUp36mkRTrRJSbYLxHDBo7MDWqU06dzvsk9t.png-normal",
      "base_zhaopian_thum": "https://media.citymiai.com/shaoxing/album/4pLvfUp36mkRTrRJSbYLxHDBo7MDWqU06dzvsk9t.png-avatar200",
      "base_xingbie": 2,
      "is_cert": 0,
      "shiming_ispass": 2,
      "base_shengri": "1995-12-19",
      "base_shuxiang": "猪",
      "base_shengao": "161",
      "work_xueli": "大专",
      "work_nianxin": "6万-8万",
      "work_danwei": "私企",
      "work_hangye": "制造业",
      "base_hunshi": "离异",
      "is_collect": false,
      "base_nianling": 25,
      "vip": null,
      "svip": null
    },
    {
      "uid": 16139,
      "base_zhaopian": "https://media.citymiai.com/shaoxing/album/PIQnKpn3S0r0jP7cTej6rEumFSkpBOoN1L1PbVav.png-normal",
      "base_zhaopian_thum": "https://media.citymiai.com/shaoxing/album/PIQnKpn3S0r0jP7cTej6rEumFSkpBOoN1L1PbVav.png-avatar200",
      "base_xingbie": 2,
      "is_cert": 0,
      "shiming_ispass": 2,
      "base_shengri": "1997-01-27",
      "base_shuxiang": "鼠",
      "base_shengao": "165",
      "work_xueli": "本科",
      "work_nianxin": "15万-20万",
      "work_danwei": "事业单位",
      "work_hangye": "医疗/健康",
      "base_hunshi": "未婚",
      "is_collect": false,
      "base_nianling": 24,
      "vip": null,
      "svip": null
    },
    {
      "uid": 14288,
      "base_zhaopian": "https://media.citymiai.com/shaoxing/album/eR1zFLTgeFia3QYCb04b1BNiqOQeD7TfgxnNCjmu.png-normal",
      "base_zhaopian_thum": "https://media.citymiai.com/shaoxing/album/eR1zFLTgeFia3QYCb04b1BNiqOQeD7TfgxnNCjmu.png-avatar200",
      "base_xingbie": 1,
      "is_cert": 0,
      "shiming_ispass": 2,
      "base_shengri": "1987-07-30",
      "base_shuxiang": "兔",
      "base_shengao": "172",
      "work_xueli": "本科",
      "work_nianxin": "10万-15万",
      "work_danwei": "事业单位",
      "work_hangye": "医疗/健康",
      "base_hunshi": "未婚",
      "is_collect": false,
      "base_nianling": 34,
      "vip": null,
      "svip": null
    },
    {
      "uid": 16462,
      "base_zhaopian": "https://media.citymiai.com/shaoxing/album/QBL1fldTjl2nBuqqQFqXQs992ocCmncT4oZ0xxos.png-normal",
      "base_zhaopian_thum": "https://media.citymiai.com/shaoxing/album/QBL1fldTjl2nBuqqQFqXQs992ocCmncT4oZ0xxos.png-avatar200",
      "base_xingbie": 2,
      "is_cert": 0,
      "shiming_ispass": 2,
      "base_shengri": "1996-10-19",
      "base_shuxiang": "鼠",
      "base_shengao": "163",
      "work_xueli": "大专",
      "work_nianxin": "8万-10万",
      "work_danwei": "国企",
      "work_hangye": "汽车/交通/运输",
      "base_hunshi": "未婚",
      "is_collect": false,
      "base_nianling": 25,
      "vip": null,
      "svip": null
    },
    {
      "uid": 12557,
      "base_zhaopian": "https://media.citymiai.com/shaoxing/album/EMuXEKscWsAG39SgTlopt54gnqaqeYZWwTMHHfpn.png-normal",
      "base_zhaopian_thum": "https://media.citymiai.com/shaoxing/album/EMuXEKscWsAG39SgTlopt54gnqaqeYZWwTMHHfpn.png-avatar200",
      "base_xingbie": 1,
      "is_cert": 0,
      "shiming_ispass": 2,
      "base_shengri": "1993-03-22",
      "base_shuxiang": "鸡",
      "base_shengao": "183",
      "work_xueli": "大专",
      "work_nianxin": "15万-20万",
      "work_danwei": "私企",
      "work_hangye": "房产建筑业",
      "base_hunshi": "未婚",
      "is_collect": false,
      "base_nianling": 28,
      "vip": null,
      "svip": null
    },
    {
      "uid": 18180,
      "base_zhaopian": "https://media.citymiai.com/shaoxing/album/39ox1a0sxMByqD78ZU4QjXMfCx67ZCILmyw5bMKn.png-normal",
      "base_zhaopian_thum": "https://media.citymiai.com/shaoxing/album/39ox1a0sxMByqD78ZU4QjXMfCx67ZCILmyw5bMKn.png-avatar200",
      "base_xingbie": 2,
      "is_cert": 0,
      "shiming_ispass": 2,
      "base_shengri": "1996-10-23",
      "base_shuxiang": "鼠",
      "base_shengao": "164",
      "work_xueli": "本科",
      "work_nianxin": "10万-15万",
      "work_danwei": "上市公司",
      "work_hangye": "金融/证券/保险",
      "base_hunshi": "未婚",
      "is_collect": false,
      "base_nianling": 25,
      "vip": null,
      "svip": null
    },
    {
      "uid": 17585,
      "base_zhaopian": "https://media.citymiai.com/images/z7dHiRFkkSzxmsE1ifXX92iKTVBwU46En4CeAWKj.png-normal",
      "base_zhaopian_thum": "https://media.citymiai.com/images/z7dHiRFkkSzxmsE1ifXX92iKTVBwU46En4CeAWKj.png-avatar200",
      "base_xingbie": 2,
      "is_cert": 0,
      "shiming_ispass": 2,
      "base_shengri": "1993-10-03",
      "base_shuxiang": "鸡",
      "base_shengao": "160",
      "work_xueli": "大专",
      "work_nianxin": "10万-15万",
      "work_danwei": "私企",
      "work_hangye": "纺织/外贸业",
      "base_hunshi": "未婚",
      "is_collect": false,
      "base_nianling": 28,
      "vip": null,
      "svip": null
    },
    {
      "uid": 18159,
      "base_zhaopian": "https://media.citymiai.com/shaoxing/album/CSzKTK6ZAUd5qX3evP5TSibmXKHWbVbX01hp4xF7.png-normal",
      "base_zhaopian_thum": "https://media.citymiai.com/shaoxing/album/CSzKTK6ZAUd5qX3evP5TSibmXKHWbVbX01hp4xF7.png-avatar200",
      "base_xingbie": 1,
      "is_cert": 0,
      "shiming_ispass": 2,
      "base_shengri": "1996-02-22",
      "base_shuxiang": "鼠",
      "base_shengao": "172",
      "work_xueli": "本科",
      "work_nianxin": "8万-10万",
      "work_danwei": "国企",
      "work_hangye": "酒店/旅游/餐饮",
      "base_hunshi": "未婚",
      "is_collect": false,
      "base_nianling": 25,
      "vip": null,
      "svip": null
    },
    {
      "uid": 17740,
      "base_zhaopian": "https://media.citymiai.com/shaoxing/album/HCUlujS4Y8qu0M1oJOYWLgrXX84goAIdqgNVsMrj.jpeg-normal",
      "base_zhaopian_thum": "https://media.citymiai.com/shaoxing/album/HCUlujS4Y8qu0M1oJOYWLgrXX84goAIdqgNVsMrj.jpeg-avatar200",
      "base_xingbie": 1,
      "is_cert": 0,
      "shiming_ispass": 2,
      "base_shengri": "1992-12-06",
      "base_shuxiang": "猴",
      "base_shengao": "176",
      "work_xueli": "本科",
      "work_nianxin": "50万以上",
      "work_danwei": "自有公司",
      "work_hangye": "纺织/外贸业",
      "base_hunshi": "未婚",
      "is_collect": false,
      "base_nianling": 28,
      "vip": {
        "vip_id": 267,
        "uid": 17740,
        "count_tuijian": 0,
        "count_wechat": 0,
        "count_toutiao": 0,
        "count_activity": 0,
        "end_time": "2022-07-22 15:32:08",
        "create_time": "2021-07-22 15:32:08",
        "update_time": "2021-07-22 15:32:08",
        "is_vip": 1,
        "count_friends": 0,
        "count_groups": 0,
        "vip_type": "Vip365"
      },
      "svip": null
    },
    {
      "uid": 18122,
      "base_zhaopian": "https://media.citymiai.com/shaoxing/album/4ehKo85hhtD1wajjbFFyrLaInpkBzKvHa49skUoO.png-normal",
      "base_zhaopian_thum": "https://media.citymiai.com/shaoxing/album/4ehKo85hhtD1wajjbFFyrLaInpkBzKvHa49skUoO.png-avatar200",
      "base_xingbie": 2,
      "is_cert": 0,
      "shiming_ispass": 2,
      "base_shengri": "1994-10-03",
      "base_shuxiang": "狗",
      "base_shengao": "160",
      "work_xueli": "本科",
      "work_nianxin": "10万-15万",
      "work_danwei": "私企",
      "work_hangye": "纺织/外贸业",
      "base_hunshi": "未婚",
      "is_collect": false,
      "base_nianling": 27,
      "vip": {
        "vip_id": 307,
        "uid": 18122,
        "count_tuijian": 0,
        "count_wechat": 1,
        "count_toutiao": 1,
        "count_activity": 3,
        "end_time": "2022-10-26 15:57:40",
        "create_time": "2021-10-26 15:57:40",
        "update_time": "2021-10-26 15:57:40",
        "is_vip": 1,
        "count_friends": 0,
        "count_groups": 0,
        "vip_type": "Vip365"
      },
      "svip": null
    },
    {
      "uid": 14133,
      "base_zhaopian": "https://media.citymiai.com/shaoxing/album/avgQKA3txFpCkQs6yukhxpQ0QP4qnYIDx9dH11xd.png-normal",
      "base_zhaopian_thum": "https://media.citymiai.com/shaoxing/album/avgQKA3txFpCkQs6yukhxpQ0QP4qnYIDx9dH11xd.png-avatar200",
      "base_xingbie": 1,
      "is_cert": 0,
      "shiming_ispass": 0,
      "base_shengri": "1996-11-06",
      "base_shuxiang": "鼠",
      "base_shengao": "178",
      "work_xueli": "本科",
      "work_nianxin": "10万-15万",
      "work_danwei": "私企",
      "work_hangye": "房产建筑业",
      "base_hunshi": "未婚",
      "is_collect": false,
      "base_nianling": 25,
      "vip": null,
      "svip": null
    },
    {
      "uid": 12022,
      "base_zhaopian": "https://media.citymiai.com/images/axm0NpTlfTtE64G8uO1MRc5sUOWAB6jEqoa0BLed.png-normal",
      "base_zhaopian_thum": "https://media.citymiai.com/images/axm0NpTlfTtE64G8uO1MRc5sUOWAB6jEqoa0BLed.png-avatar200",
      "base_xingbie": 2,
      "is_cert": 0,
      "shiming_ispass": 0,
      "base_shengri": "1994-10-29",
      "base_shuxiang": "狗",
      "base_shengao": "166",
      "work_xueli": "大专",
      "work_nianxin": "6万-8万",
      "work_danwei": "私企",
      "work_hangye": "其他",
      "base_hunshi": "未婚",
      "is_collect": false,
      "base_nianling": 27,
      "vip": null,
      "svip": null
    },
    {
      "uid": 18120,
      "base_zhaopian": "https://media.citymiai.com/shaoxing/album/jqiHivgtLgHXvaFaQveUh2BIesaZk5fVQIYyZTkQ.png-normal",
      "base_zhaopian_thum": "https://media.citymiai.com/shaoxing/album/jqiHivgtLgHXvaFaQveUh2BIesaZk5fVQIYyZTkQ.png-avatar200",
      "base_xingbie": 2,
      "is_cert": 0,
      "shiming_ispass": 2,
      "base_shengri": "1995-12-15",
      "base_shuxiang": "猪",
      "base_shengao": "160",
      "work_xueli": "本科",
      "work_nianxin": "8万-10万",
      "work_danwei": "上市公司",
      "work_hangye": "医疗/健康",
      "base_hunshi": "未婚",
      "is_collect": false,
      "base_nianling": 25,
      "vip": null,
      "svip": null
    },
    {
      "uid": 17173,
      "base_zhaopian": "https://media.citymiai.com/shaoxing/album/CIeJ5RBJCqdpMrPvisBsegd1DMWcdjnAX39LQyX5.png-normal",
      "base_zhaopian_thum": "https://media.citymiai.com/shaoxing/album/CIeJ5RBJCqdpMrPvisBsegd1DMWcdjnAX39LQyX5.png-avatar200",
      "base_xingbie": 2,
      "is_cert": 0,
      "shiming_ispass": 2,
      "base_shengri": "1996-12-10",
      "base_shuxiang": "鼠",
      "base_shengao": "162",
      "work_xueli": "本科",
      "work_nianxin": "10万-15万",
      "work_danwei": "事业单位",
      "work_hangye": "教育/培训/科研",
      "base_hunshi": "未婚",
      "is_collect": false,
      "base_nianling": 24,
      "vip": null,
      "svip": null
    }
  ]
			},
		}
	}
</script>

<style>
	page{
		background-color:#FFFFFF;
	}
</style>

<style lang="scss" scoped>
	.qiandao{
		width: 100rpx;height: 60rpx;border-radius: 30%;
	}
	
	.section{
		display: flex;justify-content: space-between;
		.section-title{
			font-size: 32rpx;color: #303133;display: flex;justify-content:center;align-items: center;
		}
		.section-right{
			font-size: 28rpx;color: #909399;
		}
	}
	
	.kite-classify-scroll {
		width: 100%;
		height: 165rpx;
		overflow: hidden;
		white-space: nowrap;
		.wall-add{
			width: 120rpx;height: 120rpx;border-radius: 100%;
		}
	}
	
	.kite-classify-cell {
		display: inline-block;
		width: 150rpx;
		height: 165rpx;
		margin-right: 20rpx;
		background-color: #ffffff;
		border-radius: 10rpx;
		overflow: hidden;
		.cell-view{
			width: 120rpx;height: 120rpx;background:linear-gradient(to bottom,#fe3ea5,#FFA500);border-radius: 100%;
			.cell-img{
				width: 115rpx;height: 115rpx;background:#FFFFFF;border-radius: 100%;
				image{
					width: 105rpx;height: 105rpx;border-radius: 100%;
				}
			}
		}
	}	
	
	.ic-img{
		display: inline-block;margin-left: 15rpx;line-height: 30rpx;
	}
</style>
