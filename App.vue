<script>
	export default {
		globalData: {
			statusBar: '',
			customBar: '',
			unread:0
		},
		onLaunch: function() {
			var that = this
			uni.getSystemInfo({
				success: function(e) {
					that.globalData.statusBar = e.statusBarHeight
					// #ifndef MP  
					if (e.platform == 'android') {
						that.globalData.customBar = e.statusBarHeight + 50
					} else {
						that.globalData.customBar = e.statusBarHeight + 45
					}
					// #endif
					// #ifdef MP-WEIXIN
					let custom = wx.getMenuButtonBoundingClientRect()
					that.globalData.customBar = custom.bottom + custom.top - e.statusBarHeight
					// #endif
				}
			})
		},
		
	}
</script>



<style lang="scss">
	/* uview 样式 */
	@import "uview-ui/index.scss";
	/* color css */
	@import "colorui/main.css";
	@import "colorui/icon.css";

</style>
