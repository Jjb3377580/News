<script>
	export default {
		onLaunch: function() {
			console.log('App Launch')
		},
		onShow: function() {
			console.log('App Show')
		},
		onHide: function() {
			console.log('App Hide')
		}
	}
</script>

<style>
	/*每个页面公共css */
	/* 1 uniapp的公共css */
	@import "./common/uni.css";
	/* 2 图标文字的css */
	@import "./common/icon.css";
	/* 3 动画css */
	@import "common/animate.css";
	/* 4 flex公共css */
	@import "common/flex.css";
	/* 导入自定义css */
	@import "./common/animate.css";
</style>
