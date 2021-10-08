<template>
  <view class="content">
    <u-swiper :list="sliderList" mode="rect" :effect3d="true"></u-swiper>
  </view>
</template>

<script>
export default {
  name: "HomeSwiper",
  data() {
    return {
      sliderList: [
        {
          image: "https://cdn.uviewui.com/uview/swiper/1.jpg",
          title: "昨夜星辰昨夜风，画楼西畔桂堂东",
        },
      ],
    };
  },
  methods: {
    GetBanner() {
      this.$u
        .get("banner", {
          type: 2,
        })
        .then((res) => {
          
          if (res.code == 200) {
            this.sliderList = [];
            for (let i = 0; i < res.banners.length; i++) {
              let element = res.banners[i];
              this.sliderList.push({
                image: element.pic,
                title: element.typeTitle,
              });
            }
            // res.banners.forEach(function(item) {
            // 	this.sliderList.push({
            // 		image: item.pic,
            // 		title: item.typeTitle
            // 	})
            // })
          }
        })
        .catch((err) => {});
      // uni.request({
      // 	url:"https://netease-cloud-music-api-alpha-virid.vercel.app/banner",
      // 	data:{
      // 		type:2
      // 	}
      // }).then(res=>{
      // 	
      // })
    },
  },
  onReady() {
    this.GetBanner();
  },
  onLoad() {
    this.GetBanner();
  },
};
</script>

<style lang="scss" scoped>
.content {
  .slider {
    width: 80%;
    border-radius: 16rpx;
    padding: 40px;
  }
}
</style>
