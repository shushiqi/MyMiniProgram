<template>
  <view class="content">
    <top-layout
      class="item"
      v-for="(item, index) in dataArr"
      :key="index"
      :top="true"
    >
      <template v-slot:img>
        <image :src="item.url" mode="" class="img"></image>
      </template>
      <template v-slot:title>
        <text class="title">{{ item.title }}</text>
      </template>
    </top-layout>
  </view>
</template>

<script>
import TopLayout from "@/components/layout/top-layout.vue";
export default {
  name: "SortMenu",
  components: {
    TopLayout,
  },
  data() {
    return {
      title: "title",
      img: "img",
      dataArr: [
        {
          url: "",
          title: "每日推荐",
        },
        {
          url: "",
          title: "私人FM",
        },
        {
          url: "",
          title: "歌单",
        },
        {
          url: "",
          title: "排行榜",
        },
        {
          url: "",
          title: "数字专辑",
        },
        {
          url: "",
          title: "专注冥想",
        },
        {
          url: "",
          title: "歌房",
        },
        {
          url: "",
          title: "游戏专区",
        },
      ],
    };
  },
};
</script>

<style lang="scss">
.content {
  width: 100%;
  height: 8rem;
  display: flex;
  justify-content: space-around;
  align-items: center;
  .item {
    width: 108rpx;
    height: 96rpx;
    border: 1px solid #000;
    .img {
      width: 32rpx;
      height: 32rpx;
    }
    .title {
      font-size: 24rpx;
      text-align: center;
    }
  }
}
</style>
