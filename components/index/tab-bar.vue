<!-- 顶部选项卡 子组件 -->
<template>
	<view class="uni-tab-bar">
		<scroll-view scroll-x="true" class="uni-swiper-tab">
			<block v-for=" (tab,index) in tabBars" :key="index">
				<!-- //每个循环得到标题 -->
				<view class="swiper-tab-list" @tap="touch(index)" :class="{'active' : tabIndex == index }">
					{{tab.name}}
					<view class="swiper-tab-bottom"></view>
				</view>
			</block>
		</scroll-view>
	</view>
	
	
</template>

<script>
	export default {
		//接收父组件传递过来的数据
		props:{
			tabBars:Array,	//选项卡分类信息的数据
			tabIndex:Number	//顶部选项卡激活选择位置
		},
		data() {
			return {
				
			};
		},
		methods:{
			// 当手指触碰标题的时候,切换到当前的标题
			touch(index) {
				//子组件不好修改父组件的变量
				// this.tabIndex = index
				
				this.$emit("toFather",index)
			},
		}
	}
</script>

<style scoped>
	
	/* 顶部选项卡 */
	/*导航条激活点击状态*/
	.uni-tad-bar.active {
		color: #8F8F94;
	}
	
	/*导航字体*/
	.swiper-tab-list {
		color: #969696;
		font-weight: bold;
	}
	
	/*导航边框颜色*/
	.uni-swiper-tab {
		border-bottom: 1upx solid #EEEEEE;
	}
	
	/*激活时候才有黄色条样式*/
	.active .swiper-tab-bottom {
		border-bottom: 6upx solid #FFA411;
		width: 70upx;
		margin: 0 auto;
		border-radius: 20upx;
	}
	
	

</style>
