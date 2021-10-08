<template>
  <view class="container">
    <view class="silder">
      <!-- <u-swiper :list="sliderList" mode="rect" :effect3d="true"></u-swiper> -->
      <home-swiper></home-swiper>
    </view>
    <view class="top_menu">
      <sort-menu></sort-menu>
    </view>
    <u-divider border-color="#6d6d6d" half-width="50%" use-slot="false"></u-divider>
	<view class="recommended_playlist">
      <recommond-list></recommond-list>
    </view>
    <view class="featured_playlist"> </view>
    <view class="leaderboard"> </view>
    <!-- <u-gap height="70"></u-gap> -->
  </view>
</template>

<script>
import HomeSwiper from "./components/home-swiper.vue";
import SortMenu from "./components/sort-menu.vue";
import RecommondList from "./components/recommend-list.vue";
export default {
  components: {
    HomeSwiper,
    SortMenu,
    RecommondList,
  },
  data() {
    return {};
  },
  methods: {},
  onReady() {},
  onLoad() {},
};
</script>

<style lang="scss" scoped>
.container {
  width: 100%;
  height: 100%;
  background-color: #f6f3f3f1;
 .slider {
    width: 80%;
    border-radius: 16rpx;
    padding: 40px;
  }
  .top_menu {
    width: 170%;
    // height: 60rpx;
  }
  .recommended_playlist{
	  width: 100%;
  }
}
</style>
