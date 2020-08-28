<template>
	
		<!-- 新闻大框 某个新闻 -->
		<view class="index-list animated rotateIn slow">
			<!-- 第一行 -->
			<view class="index-list1">
				<!-- 左边 -->
				<view>
					<!-- 头像 -->
					<image :src="item.userpic" mode="widthFix"></image>{{item.username}}
				</view>
	
				<!-- 右边 -->
				<view @tap="guanZhu" v-show="!item.isGuanzhu">
					<view class="icon iconfont icon-zengjia"></view>关注
				</view>
	
			</view>
			<!-- 第二行 -->
			<view class="index-list2" @tap="openDetail">
				{{item.title}}
			</view>
			<!-- 第三行 -->
			<view class="index-list3" @tap="openDetail">
				<image :src="item.titPic" mode="widthFix"></image>
				<!-- 播放按钮 -->
				<view class="icon iconfont icon-bofang"></view>
				<!-- 播放量和时长 -->
				<view>{{item.playNum}}次播放量 {{item.videoLong}}</view>
			</view>
			<!-- 第四行 -->
			<view class="index-list4 t1">
				<!-- 左边 -->
				<view class="t1">
					<!-- 笑脸 -->
					<view @tap="chuPeng('ding')" class="t1" :class="{ 'active':(item.infonNum.index ==1 )}">
						<view class="icon iconfont icon-icon_xiaolian-mian"></view>{{item.infonNum.dingNum}}
					</view>
					<!-- 哭脸 -->
					<view @tap="chuPeng('cai')" class="t1" :class="{ 'active':(item.infonNum.index ==2 )}">
						<view class="icon iconfont icon-kulian"></view>{{item.infonNum.caiNum}}
					</view>
				</view>
	
				<!-- 右边 -->
				<view class="t1">
					<!-- 评论 -->
					<view class="t1">
						<view class="icon iconfont icon-pinglun1"></view>{{item.commentNum}}
					</view>
					<!-- 转发 -->
					<view class="t1">
						<view class="icon iconfont icon-zhuanfa"></view>{{item.shareNum}}
					</view>
				</view>
			</view>
	
		</view>
		
	
</template>

<script>
	export default {
		// 子主键接收父组件的数据
		props: {
			item : Object  ,	//对象数据类型
			index : Number		//Number数字类型
		},
		data() {
			return {
				
			};
		},
		
		methods:{
			guanZhu(){
				uni.showToast({
					title:"关注成功!"
				})
				this.item.isGuanzhu=true
			},
			
			//顶踩操作
			chuPeng(type){
				switch(type){
					case "ding":
					if(this.item.infonNum.index==0){
						// this.item.infonNum.caiNum--
						this.item.infonNum.dingNum++
						this.item.infonNum.index=1
					}
					else if(this.item.infonNum.index==2){
						 this.item.infonNum.caiNum--
						this.item.infonNum.dingNum++
						this.item.infonNum.index=1
					}
					else if(this.item.infonNum.index==1){
						// this.item.infonNum.caiNum--
						this.item.infonNum.dingNum++
						this.item.infonNum.index=0
					}
					
					break;
					
					case "cai":
					if(this.item.infonNum.index==0){
						this.item.infonNum.caiNum--
						// this.item.infonNum.dingNum++
						this.item.infonNum.index=1
					}
					else if(this.item.infonNum.index==2){
						 this.item.infonNum.caiNum--
						//this.item.infonNum.dingNum++
						this.item.infonNum.index=0
					}
					else if(this.item.infonNum.index==1){
						 this.item.infonNum.caiNum--
						this.item.infonNum.dingNum++
						this.item.infonNum.index=2
					}
					break;
					
				}
				
			},
			
			//点击打开具体界面
			openDetail(){
				uni.uni.showToast({
					title: "正在打开当前页面",
					icon:"loading"
				});	
			}
		}
	}
</script>

<!-- scoped当前css私有化 -->
<style scoped>
	/* 新闻大框 */
	.index-list {
		padding: 20upx;
		border-bottom: 1upx solid #EEEEEE;
	}
	/* 第一行 */
	.index-list1{
		display: flex;
		justify-content: space-between;
		align-items: center;
	}
	/* 第一行文字 */
	.index-list1>view {
		display: flex;
		justify-content: space-between;
		align-items: center;
	}
	/*第一行图片头像*/
	.index-list1>view:first-child image {
		width: 90upx;
		height: 90upx;
		border-radius: 50%;
		margin-right: 16upx;
	}
	
	/*第一行 右边*/
	.index-list1>view:first-child {
		color: #989898;
	}
	
	/*第一行 右边*/
	.index-list1>view:last-child {
		background: #CCCCCC;
		border-radius: 4upx;
		padding-left: 16upx;
		padding-right: 16upx;
	}
	/* 第二行 */
	.index-list2 {
		margin-top: 16upx;
		font-size: 32upx;
	}
	
	/* 第三行 */
	.index-list3 {
		margin-top: 20upx;
		position: relative;
	}
	
	/*第三行 播放按钮*/
	.icon-bofang {
		position: absolute;
		font-size: 150upx;
		color: #FFFFFF;
		top: 18%;
		left: 40%
	}
	
	/*第三行 播放时长、播放量*/
	.index-list3>view:nth-of-type(2) {
		position: absolute;
		background: #000000;
		border-radius: 40upx;
		color: #FFFFFF;
		right: 20upx;
		bottom: 30upx;
		font-size: 24upx;
		padding-left: 16upx;
		padding-right: 16upx;
		opacity: 0.7;
	}
	
	/*第三行图片*/
	.index-list3>image {
		width: 100%;
		border-radius: 20upx;
	}
	
	/*第四行 笑脸哭脸   评论转发*/
	.index-list4>view>view>view {
		font-size: 26upx;
		margin-right: 14upx;
		margin-left: 14upx;
	}
	
	.active {
		color: #FFB400;
	}
	.swiper-box {
		height: 3000upx;
	}
	.t1 {
		display: flex;
		justify-content: space-between;
		align-items: center;
	}

</style>
