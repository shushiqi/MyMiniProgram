<template>
	<view class="content">
		<view class="list-info">
			<view class="bgImg" :style="{
          backgroundImage: `url(${backgroundImage})`,
          backgroundSize: '100% 100%',
        }">
			</view>
			<view class="left-cover">
				<u-image width="200rpx" height="200rpx" border-radius="32" class="cover" :src="playlist.coverImgUrl">
				</u-image>
				<u-badge type="info" :count="playlist.playCount"></u-badge>
			</view>
			<view class="right-info">
				<text class="name">{{ playlist.name }}</text>
				<view class="creator">
					<view class="creator-avartar">
						<u-image width="80rpx" height="80rpx" border-radius="16" class="cover"
							:src="playlist.creator.avatarUrl">
						</u-image>
					</view>
					<view class="creator-name">
						<text>{{ playlist.creator.nickname }}</text>
					</view>
					<!-- <image src="" mode="" class="subscribe-icon"></image> -->
				</view>
				<view class="description">
					<text>{{ playlist.description ? playlist.description : "" }}</text>
				</view>
			</view>
		</view>
		<view class="button-group">
			<view class="subscribe button">
				<u-icon :name="playlist.subscribed ? 'star-fill' : 'star'" size="mini"></u-icon>
				{{ playlist.subscribedCount }}
			</view>
			<view class="comment button">
				<u-icon name="chat" size="mini"></u-icon>{{ playlist.commentCount }}
			</view>
			<view class="share button">
				<u-icon name="share" size="mini"></u-icon>{{ playlist.shareCount }}
			</view>
		</view>
		<scroll-view class="song-list">
			<view class="control"> </view>
			<view class="songs">
				<view class="song" v-for="(item, index) in song" :key="index">
					<view class="song-ord">
						<text>{{ index+1 }}</text>
					</view>
					<song class="song-info" :infoObj="item"></song>
				</view>
			</view>
		</scroll-view>
	</view>
</template>

<script>
	import divider from "@/components/divider.vue";
	import Song from "@/components/song.vue";
	export default {
		name: "song-list-detail",
		components: {
			divider,
			Song,
		},
		data() {
			return {
				id: "",
				playlist: {
					subscribedCount: 0,
					commentCount: 0,
					shareCount: 0,
				},
				infoBG: {
					width: "100%",
					height: "100%",
					backgroundSize: "cover",
				},
				backgroundImage: "",
				song: [],
			};
		},
		onLoad(options) {
			console.log(options);
			this.id = options.id;
			this.$u
				.get("playlist/detail", {
					id: this.id,
				})
				.then((res) => {
					if (res.code == 200) {
						console.log(res);
						this.playlist = res.playlist;
						this.backgroundImage = res.playlist.coverImgUrl;
						if (res.playlist.tracks.length > 0) {
							this.song = [];
							for (let i = 0; i < res.playlist.tracks.length; i++) {

								let element = res.playlist.tracks[i];
								if (element.alia.length > 0) {
									element.name = `${element.name}(${element.alia[0]})`
								}
								this.song.push({
									cover: element.al.picUrl,
									name: element.name,
									singer: element.ar[0].name,
									album: element.al.name,
								});
							}
						}
					}
				});
		},
	};
</script>

<style lang="scss">
	.content {
		display: flex;
		flex-wrap: wrap;
		justify-content: center;

		.list-info {
			width: 100%;
			height: 300rpx;
			display: flex;
			justify-content: flex-start;
			align-items: center;
			padding: 0 5%;

			.bgImg {
				width: 100%;
				height: 300rpx;
				position: absolute;
				left: 0;
				top: 0;
				filter: blur(25px);
				z-index: -1;
			}

			.left-cover {
				width: 30%;
				height: 200rpx;
				position: relative;
			}

			.right-info {
				margin-left: 16rpx;
				width: 60%;
				height: 200rpx;
				display: flex;
				flex-direction: column;
				justify-content: flex-start;
				align-items: flex-start;

				.name {
					font-size: 30rpx;
				}

				.creator {
					width: 100%;
					display: flex;
					justify-content: flex-start;
					align-items: center;
					font-size: 24rpx;

					&-name {
						flex: 1;
					}
				}

				.description {
					width: 100%;
					height: 40rpx;
					// overflow: hidden;
					text-overflow: ellipsis;
					overflow: hidden;
					white-space: nowrap;
					z-index: 99;
				}
			}
		}

		.button-group {
			width: 70%;
			height: 60rpx;
			border: 1px solid #000000;
			background-color: #ffffff;
			border-radius: 50px;
			display: flex;
			justify-content: space-around;
			align-items: center;
			position: relative;
			top: 60rpx;
			margin-bottom: 32rpx;

			.button {
				width: 30%;
				display: flex;
				justify-content: center;
			}

			.subscribe {
				border-right: 1px solid #E5E5E5;
			}

			.comment {
				border-right: 1px solid #E5E5E5;
			}
		}

		.song-list {
			width: 100%;
			// height: 600rpx;
			background-color: #ffffff;

			.songs {
				display: flex;
				flex-wrap: wrap;
				justify-content: flex-start;
				align-items: center;

				.song {
					width: 100%;
					height: 120rpx;
					display: flex;
					justify-content: center;
					align-items: center;

					&-ord {
						width: 5%;

						font-size: 48rpx;
						color: #999999;
						text-align: center;
					}

					&-info {
						width: 90%;
					}
				}
			}
		}
	}
</style>
