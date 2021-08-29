<template>
	<view class="container">
		<view class="silder">
			<u-swiper :list="sliderList" mode="rect" :effect3d="true"></u-swiper>
		</view>
		<view class="top_menu">

		</view>
		<view class="recommended_playlist">

		</view>
		<view class="featured_playlist">

		</view>
		<view class="leaderboard">

		</view>
		<!-- <u-gap height="70"></u-gap> -->
	</view>
</template>

<script>
	export default {
		data() {
			return {
				sliderList: [{
						image: 'https://cdn.uviewui.com/uview/swiper/1.jpg',
						title: '昨夜星辰昨夜风，画楼西畔桂堂东'
					},
					{
						image: 'https://cdn.uviewui.com/uview/swiper/2.jpg',
						title: '身无彩凤双飞翼，心有灵犀一点通'
					},
					{
						image: 'https://cdn.uviewui.com/uview/swiper/3.jpg',
						title: '谁念西风独自凉，萧萧黄叶闭疏窗，沉思往事立残阳'
					}
				],
			};
		},
		methods: {
			GetBanner() {
				// this.$u.get("banner", {
				// 	type: 2
				// }).then(res => {
				// 	console.log(res)
				// 	if (res.code == 200) {
				// 		this.sliderList = []
				// 		res.banners.forEach(function(item){
				// 			this.sliderList.push({
				// 				image: item.pic,
				// 				title: item.typeTitle
				// 			})
				// 		})					
				// 	}
				// })
				uni.request({
					url:"https://netease-cloud-music-api-alpha-virid.vercel.app/banner",
					data:{
						type:2
					}
				}).then(res=>{
					console.log(res)
				})
			}
		},
		onReady() {},
		onLoad() {
			this.GetBanner()
		}
	}
</script>

<style lang="scss" scoped>
	.container {
		.slider {
			width: 80%;
			border-radius: 16rpx;
			padding: 40px;
		}
	}
</style>
