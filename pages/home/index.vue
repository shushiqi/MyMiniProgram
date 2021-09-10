<template>
	<view class="container">
		<view class="silder">
			<!-- <u-swiper :list="sliderList" mode="rect" :effect3d="true"></u-swiper> -->
			<home-swiper></home-swiper>
		</view>
		<view class="top_menu">
			<top-layout >
				<text v-slot="title">每日推荐</text>
			</top-layout>
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
	import HomeSwiper from "./components/home-swiper.vue"
	import TopLayout from "@/components/layout/top-layout.vue"
	export default {
		components:{
			HomeSwiper,
			TopLayout
		},
		data() {
			return {
				
			};
		},
		methods: {
			
		},
		onReady() {},
		onLoad() {
			
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
