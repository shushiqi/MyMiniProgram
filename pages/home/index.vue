<template>
  <view class="container">
    <view class="">
      <u-form :model="form" ref="uForm">
        <u-form-item label="查询" prop="name">
          <u-input v-model="form.name" />
        </u-form-item>
      </u-form>
      <u-button @click="submit">提交</u-button>
    </view>
    <view class="songs">
      <view class="song_item" v-for="(item, index) in songs" :key="index">
        <view class="song_name">
          <text>{{ item.name }}</text>
        </view>
        <view class="song_singer">
          <text>{{ item.artists[0].name }}</text>
        </view>
      </view>
    </view>
  </view>
</template>

<script>
export default {
  data() {
    return {
      songs: {},
      form: {
        name: "",
        intro: "",
      },
      rules: {
        name: [
          {
            required: true,
            message: "请输入关键词",
            // 可以单个或者同时写两个触发验证方式
            trigger: ["change", "blur"],
          },
        ],
        intro: [
          {
            min: 5,
            message: "简介不能少于5个字",
            trigger: "change",
          },
        ],
      },
    };
  },
  methods: {
    submit() {
      this.$refs.uForm.validate((valid) => {
        if (valid) {
          // console.log('验证通过');
          // this.$requst("search", {
          // 	keywords: this.form.name
          // }).then(res => {
          // 	this.songs = res.data
          // })
          this.$u
            .get("search", {
              keywords: this.form.name,
            })
            .then((res) => {
              console.log(res);
              this.songs = res.result.songs;
            });
        } else {
          console.log("验证失败");
        }
      });
    },
  },
  onReady() {
    this.$refs.uForm.setRules(this.rules);
  },
};
</script>

<style lang="scss" scoped>
.container {
  .songs {
    width: 100%;
    display: flex;
    justify-content: flex-start;
    flex-wrap: wrap;
    .song_item {
      width: 100%;
      
      display: flex;
      justify-content: flex-start;
	  .song_name{
		  width: 50%;
	  }
	  .song_singer{
		  width: 50%;
	  }
    }

  }
}
</style>
