<template>
	<view class="content">
		<view class="cover">
			<u-image width="100rpx" height="100rpx" border-radius="32" class="cover" v-if="coverShow" :src="cover">
			</u-image>
		</view>
		<view class="info">
			<view class="song-name">
				<text>{{name}}</text>
			</view>
			<view class="singer">
				<text>{{singer}}</text>- <text>{{album}}</text>
			</view>
		</view>
		<view class="menu">
			<view class="video">

			</view>
			<view class="option">

			</view>
		</view>
	</view>
</template>

<script>
	export default {
		name: "Song",
		props: {
			ids: {
				type: String,
				default: "",
			},
			coverShow: {
				type: Boolean,
				default: true,
			},

			infoObj: {
				type: Object,
				default: () => ({}),
			},
		},
		data() {
			return {
				cover: "",
				name: "",
				singer: "",
				album: ""
			};
		},
		onLoad() {
			if (Object.keys(this.infoObj).length === 0) {
				this.cover = this.infoObj.cover
				this.name = this.infoObj.name
				this.singer = this.infoObj.singer
				this.album = this.infoObj.album
			} else {
				this.$u
					.get("song/detail", {
						// ids: this.ids,
						ids: "347230,347231",
					})
					.then((res) => {
						if (res.code == 200) {
							console.log(res);
							if (res.songs.length > 0) {

							}
						}
					});
			}
		},
	};
</script>

<style lang="scss" scoped>
	.content {
		width: 100%;
		height: 120rpx;
		display: flex;
		justify-content: flex-start;
		align-items: center;

		.cover {
			margin: 0 16rpx;
		}

		.info {
			flex: 1;
		}

		.menu {
			width: 20%;
		}
	}
</style>
