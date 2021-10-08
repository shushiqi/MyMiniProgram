<template>
	<view class="content">
		<view class="list-info">
			<view class="bgImg" :style="{backgroundImage: `url(${backgroundImage})`, backgroundSize:'100% 100%' }">
			</view>
			<view class="left-cover">
				<u-image width="100px" height="100px" border-radius="32" class="cover" :src="playlist.coverImgUrl">
				</u-image>
				<u-badge type="info" :count="playlist.playCount"></u-badge>
			</view>
			<view class="right-info">
				<text class="name">{{playlist.name}}</text>
				<view class="creator">
					<view class="creator-avartar">
						<u-image width="40px" height="40px" border-radius="16" class="cover"
							:src="playlist.creator.avatarUrl">
						</u-image>
					</view>
					<view class="creator-name">
						<text>{{playlist.creator.nickname}}</text>
					</view>
					<!-- <image src="" mode="" class="subscribe-icon"></image> -->
				</view>
				<view class="description">
					<text>{{playlist.description?playlist.description:""}}</text>
				</view>
			</view>
		</view>
		<scroll-view class="song-list">
			<view class="button-group">
				<view class="subscribe">
					<u-icon :name="playlist.subscribed? 'star-fill':'star'" size="mini"></u-icon>
					{{playlist.subscribedCount}}
				</view>
				<view class="comment">
					<u-icon name="chat" size="mini"></u-icon>{{playlist.commentCount}}
				</view>
				<view class="share">
					<u-icon name="share" size="mini"></u-icon>{{playlist.commentCount}}{{playlist.shareCount}}
				</view>
			</view>
			<view class="songs">

			</view>
		</scroll-view>
	</view>
</template>

<script>
	import divider from "@/components/divider.vue"
	export default {
		name: "song-list-detail",
		components: {
			divider
		},
		data() {
			return {
				id: "",
				playlist: {},
				infoBG: {
					width: "100%",
					height: "100%",
					backgroundSize: "cover",
				},
				backgroundImage: "",

			};
		},
		onLoad(options) {
			console.log(options)
			this.id = options.id
			this.$u.get("playlist/detail", {
				id: this.id
			}).then(res => {
				if (res.code == 200) {
					console.log(res)
					this.playlist = res.playlist
					this.backgroundImage = res.playlist.coverImgUrl
				}
			})
		},

	}
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



		.song-list {
			width: 100%;
			height: 600rpx;
			background-color: #FFFFFF;
				

			.button-group {
				width: 70%;
				height: 60rpx;
				border: 1px solid #000000;
				background-color: #FFFFFF;
				border-radius: 50px;
				display: flex;
				justify-content: space-around;
				align-items: center;
				position: relative;
				left: 50%;
				transform: translate(-50%, 0);
				z-index: 9999;
			}
		}


	}
</style>
