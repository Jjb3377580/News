<template>
	<view class="me-list">
		<view class="me-list1">
			登录有你想看的，嘿嘿嘿！
		</view>

		<view class="me-list2">
			<view class="icon iconfont icon-weixin"></view>
			<view class="icon iconfont icon-QQ"></view>
			<view class="icon iconfont icon-xinlangweibo"></view>
		</view>

		<view class="me-list3">
			账号密码登录<view class="icon iconfont icon-jinru"></view>
		</view>

		<view class="me-list4">

			<view>
				<view>0</view>
				<view>百事</view>
			</view>

			<view>
				<view>0</view>
				<view>动态</view>
			</view>

			<view>
				<view>0</view>
				<view>评论</view>
			</view>

			<view>
				<view>0</view>
				<view>收藏</view>
			</view>
		</view>

		<view class="me-list5">
			<image src="../../static/demo/datapic/3.jpg"></image>
		</view>

		<view class="me-list6">
			<!-- 左边 -->
			<view class="icon iconfont icon-liulan">浏览历史</view>
			<!-- 右边 -->
			<view class="icon iconfont icon-jinru"></view>
		</view>

		<view class="me-list7">
			<!-- 左边 -->
			<view class="icon iconfont icon-huiyuanvip">百认证</view>
			<!-- 右边 -->
			<view class="icon iconfont icon-jinru"></view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {

			}
		},
		methods: {}
	}
</script>

<style>
	.me-list {
		margin: 20upx;
	}

	.me-list1 {
		font-size: 32upx;
		text-align: center;
	}

	.me-list2 {
		display: flex;
		justify-content: space-between;
		align-items: center;
		margin-top: 40upx;
	}
	
	/* 图标的布局 */
	.me-list2>view {
		padding: 30upx 48upx 30upx 53upx;
		font-size: 50upx;
	}
	
	/* 第一个图标 */
	.me-list2>view:nth-child(1){
		background-color: #5ddf87;
		border-radius: 50%;
		color: #FFFFFF;
	}
	/* 第二个图标 */
	.me-list2>view:nth-child(2){
		background-color: #00aaff;
		border-radius: 50%;
		color: #FFFFFF;
	}
	/* 第三个图标 */
	.me-list2>view:nth-child(3){
		background-color: #ff860c;
		border-radius: 50%;
		color: #FFFFFF;
	}

	.me-list3 {
		font-size: 28upx;
		color: #3F536E;
		display: flex;
		justify-content: space-between;
		align-items: center;
		padding-right: 36%;
		padding-left: 35%;
		margin-top: 80upx;
	}

	.me-list4 {
		display: flex;
		justify-content: space-between;
		align-items: center;
		padding: 50upx;
	}

	.me-list4>view {
		text-align: center;
	}

	.me-list5>image {
		width: 100%;
		height: 350upx;
	}

	.me-list6 {
		display: flex;
		justify-content: space-between;
		align-items: center;
		font-size: 24upx;
		padding-top: 20upx;
	}

	.me-list6>view {
		color: #007AFF;
	}

	.me-list7 {
		display: flex;
		justify-content: space-between;
		align-items: center;
		font-size: 24upx;
		padding-top: 20upx;
	}

	.me-list7>view {
		color: #DD524D;
	}
</style>
