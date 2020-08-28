<template>
	<view>
		
		<!-- 顶部选项卡 -->
		<tabbar :tabBars="tabBars" :tabIndex="tabIndex" @toFather="syn_tabIndex"></tabbar>
		
		<!-- indicator-dots 指示点
		autoplay 自动播放
		interval 滑块的切换时间
		duration 切换动画时长
		 -->
		 <view class="uni-tab-bar">
			 <!-- current代表当前swiper在第几个滑块 -->
		 	<swiper :duration="500" class="swiper-box" :style="{height : swiperHeight+'px'}" :current="tabIndex" @change="tanChange">
		 		<!-- 第一层循环：循环全部分类 -->
		 		<swiper-item v-for="(items,sortIndex) in newsSortList" :key="sortIndex">
					<block v-if="items.list.length>0">
				<scroll-view scroll-y="true" class="list">
					<block v-for="(item , index)  in items.list" :key="index">
						<newslist :item="item" :index="index"></newslist>
					</block>
				</scroll-view>
					</block>
					<block v-else>
						<nothing></nothing>
					</block>
		 		</swiper-item>
		 
		 	</swiper>
		 </view>
		
		<!-- 第一层循环：循环全部分类 -->
		<block>
			<!-- 第二层循环，循环单个分类 -->
	
		</block>
	
	
	</view>
	
</template>

<script>
	import newslist from "../../components/index/news-list.vue"
	import tabbar   from"../../components/index/tab-bar.vue"
	import nothing	from"../../components/common/nothing.vue"

	export default {
		// 引用组件到当前页面
		components: {
			newslist,
			tabbar,
			nothing
		},

		data() {
			return {
				//激活当前标题
				tabIndex: 1,
				swiperHeight:2000,
				
				//全部分类的新闻数据
				newsSortList: [
					{
						//关注分类数据
						list: [
							//第一个新闻 
							{
								userpic: "../../static/demo/topicpic/8.jpeg", //头像图片
								username: "1", //昵称
								isGuanzhu: true, //是否已关注
								title: "很无聊",
								titPic: "../../static/demo/datapic/2.jpg", //新闻图片
								type: "video", // video视频类型   img图片类型
								infonNum: {
									dingNum: 231, //顶数量
									caiNum: 44, //踩数量
									index: 2 //是否已经顶或踩   0没有操作    1顶     2踩
								},
								commentNum: 999, //评论数量
								shareNum: 0, //转发数量
								playNum: 0, //播放次数
								videoLong: "4：10" //视频长度
							},
							//第二个新闻
							{
								userpic: "../../static/demo/userpic/15.jpg", //头像图片
								username: "2", //昵称
								isGuanzhu: false, //是否已关注
								title: "开心的一天",
								titPic: "../../static/demo/datapic/35.jpg", //新闻图片
								type: "video", // video视频类型   img图片类型
								infonNum: {
									dingNum: 44212, //顶数量
									caiNum: 3, //踩数量
									index: 1 //是否已经顶或踩   0没有操作    1顶     2踩
								},
								commentNum: 23, //评论数量
								shareNum: 42425, //转发数量
								playNum: 6343, //播放次数
								videoLong: "5:51" //视频长度
							},
							//第三个新闻
							{
								userpic: "../../static/demo/topicpic/9.jpeg", //头像图片
								username: "3", //昵称
								isGuanzhu: true, //是否已关注
								title: "学习使我快乐",
								titPic: "../../static/demo/datapic/37.jpg", //新闻图片
								type: "video", // video视频类型   img图片类型
								infonNum: {
									dingNum: 666, //顶数量
									caiNum: 0, //踩数量
									index: 1 //是否已经顶或踩   0没有操作    1顶     2踩
								},
								commentNum: 6, //评论数量
								shareNum: 666, //转发数量
								playNum: 4400, //播放次数
								videoLong: "4:23", //视频长度
							},
							//第四个新闻
							{
								userpic: "../../static/demo/topicpic/19.jpeg", //头像图片
								username: "4", //昵称
								isGuanzhu: true, //是否已关注
								title: "小小心意不成敬意。",
								titPic: "../../static/demo/datapic/46.jpg", //新闻图片
								type: "video", // video视频类型   img图片类型
								infonNum: {
									dingNum: "13W", //顶数量
									caiNum: "35W", //踩数量
									index: 2 //是否已经顶或踩   0没有操作    1顶     2踩
								},
								commentNum: "27W", //评论数量
								shareNum: "2W", //转发数量
								playNum: "45W", //播放次数
								videoLong: "23:12", //视频长度
							}
						]
					},
					{
						//推荐分类数据
						list: [
							//第一个新闻 
							{
								userpic: "../../static/demo/topicpic/8.jpeg", //头像图片
								username: "小六子", //昵称
								isGuanzhu: false, //是否已关注
								title: "很无聊",
								titPic: "../../static/demo/datapic/2.jpg", //新闻图片
								type: "video", // video视频类型   img图片类型
								infonNum: {
									dingNum: 231, //顶数量
									caiNum: 44, //踩数量
									index: 2 //是否已经顶或踩   0没有操作    1顶     2踩
								},
								commentNum: 999, //评论数量
								shareNum: 0, //转发数量
								playNum: 0, //播放次数
								videoLong: "4：10" //视频长度
							},
							//第二个新闻
							{
								userpic: "../../static/demo/userpic/15.jpg", //头像图片
								username: "二愣子", //昵称
								isGuanzhu: true, //是否已关注
								title: "开心的一天",
								titPic: "../../static/demo/datapic/35.jpg", //新闻图片
								type: "video", // video视频类型   img图片类型
								infonNum: {
									dingNum: 44212, //顶数量
									caiNum: 3, //踩数量
									index: 1 //是否已经顶或踩   0没有操作    1顶     2踩
								},
								commentNum: 23, //评论数量
								shareNum: 42425, //转发数量
								playNum: 6343, //播放次数
								videoLong: "5:51" //视频长度
							},
							//第三个新闻
							{
								userpic: "../../static/demo/topicpic/9.jpeg", //头像图片
								username: "三娃子", //昵称
								isGuanzhu: true, //是否已关注
								title: "学习使我快乐",
								titPic: "../../static/demo/datapic/37.jpg", //新闻图片
								type: "video", // video视频类型   img图片类型
								infonNum: {
									dingNum: 666, //顶数量
									caiNum: 0, //踩数量
									index: 1 //是否已经顶或踩   0没有操作    1顶     2踩
								},
								commentNum: 6, //评论数量
								shareNum: 666, //转发数量
								playNum: 4400, //播放次数
								videoLong: "4:23", //视频长度
							},
							//第四个新闻
							{
								userpic: "../../static/demo/topicpic/19.jpeg", //头像图片
								username: "胡桃夹子", //昵称
								isGuanzhu: true, //是否已关注
								title: "小小心意不成敬意。",
								titPic: "../../static/demo/datapic/46.jpg", //新闻图片
								type: "video", // video视频类型   img图片类型
								infonNum: {
									dingNum: "13W", //顶数量
									caiNum: "35W", //踩数量
									index: 2 //是否已经顶或踩   0没有操作    1顶     2踩
								},
								commentNum: "27W", //评论数量
								shareNum: "2W", //转发数量
								playNum: "45W", //播放次数
								videoLong: "23:12", //视频长度
							}
						]
					},
					{
						//体育分类数据
						list: [
							//第一个新闻 
							{
								userpic: "../../static/demo/topicpic/8.jpeg", //头像图片
								username: "小1", //昵称
								isGuanzhu: true, //是否已关注
								title: "很无聊",
								titPic: "../../static/demo/datapic/2.jpg", //新闻图片
								type: "video", // video视频类型   img图片类型
								infonNum: {
									dingNum: 231, //顶数量
									caiNum: 44, //踩数量
									index: 2 //是否已经顶或踩   0没有操作    1顶     2踩
								},
								commentNum: 999, //评论数量
								shareNum: 0, //转发数量
								playNum: 0, //播放次数
								videoLong: "4：10" //视频长度
							},
							//第二个新闻
							{
								userpic: "../../static/demo/userpic/15.jpg", //头像图片
								username: "二2", //昵称
								isGuanzhu: true, //是否已关注
								title: "开心的一天",
								titPic: "../../static/demo/datapic/35.jpg", //新闻图片
								type: "video", // video视频类型   img图片类型
								infonNum: {
									dingNum: 44212, //顶数量
									caiNum: 3, //踩数量
									index: 1 //是否已经顶或踩   0没有操作    1顶     2踩
								},
								commentNum: 23, //评论数量
								shareNum: 42425, //转发数量
								playNum: 6343, //播放次数
								videoLong: "5:51" //视频长度
							},
							//第三个新闻
							{
								userpic: "../../static/demo/topicpic/9.jpeg", //头像图片
								username: "三3", //昵称
								isGuanzhu: true, //是否已关注
								title: "学习使我快乐",
								titPic: "../../static/demo/datapic/37.jpg", //新闻图片
								type: "video", // video视频类型   img图片类型
								infonNum: {
									dingNum: 666, //顶数量
									caiNum: 0, //踩数量
									index: 1 //是否已经顶或踩   0没有操作    1顶     2踩
								},
								commentNum: 6, //评论数量
								shareNum: 666, //转发数量
								playNum: 4400, //播放次数
								videoLong: "4:23", //视频长度
							},
							//第四个新闻
							{
								userpic: "../../static/demo/topicpic/19.jpeg", //头像图片
								username: "胡4", //昵称
								isGuanzhu: true, //是否已关注
								title: "小小心意不成敬意。",
								titPic: "../../static/demo/datapic/46.jpg", //新闻图片
								type: "video", // video视频类型   img图片类型
								infonNum: {
									dingNum: "13W", //顶数量
									caiNum: "35W", //踩数量
									index: 2 //是否已经顶或踩   0没有操作    1顶     2踩
								},
								commentNum: "27W", //评论数量
								shareNum: "2W", //转发数量
								playNum: "45W", //播放次数
								videoLong: "23:12", //视频长度
							}
						]
					},
					{
						//热点分类数据
						list: [ ]
					},
					{
						//动漫分类数据
						list: [ ]
					},
					{
						//娱乐分类数据
						list: [ ]
					}
				],



				//顶部横向导航
				tabBars: [{
						name: "关注",
						id: "guanzhu"
					},
					{
						name: "推荐",
						id: "tuijian"
					},
					{
						name: "体育",
						id: "tiyu"
					},
					{
						name: "热点",
						id: "redian"
					},
					{
						name: "动漫",
						id: "dongm"
					},
					{
						name: "娱乐",
						id: "yule"
					}
				]
			}
		},
		onLoad() {
			uni.getSystemInfo({
				success: (res) => {
					console.log(res.screenWidth)
					console.log(res.screenHeight)
					console.log("---------------")
					console.log(res.windowWidth)
					console.log(res.windowHeight)

					this.swiperHeight = 400 * 3
				}
			})
		},
		methods: {
			//监听并处理子组件传递过来的数据
			//同步用户触碰的分类标题下标
			syn_tabIndex(index){
				this.tabIndex=index
			},
			
			//用手指切换swiper组件的时候，触发该事件
			// 顺便把上面的顶部选项卡选中下标也切换
			tabChange(event){
				console.log("swiper切换到第"+event.detail.current+"个滑块")
				this.tabIndex = event.detail.current
			}
		}
	}
</script>

<style>
	/* swiper样式 */
	



	
</style>
