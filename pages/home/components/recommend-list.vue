<template>
	<view class="content">
		<view class="title">
			<text>推荐歌单</text>
		</view>
		<view class="list">
			<view class="list-item" v-for="(item,index) in list" :key="index" @click="toListDetail(item.id)">
				<image class="img" :src="item.picUrl" mode=""></image>
				<text class="name">{{item.name}}</text>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		name: "RecommondList",
		data() {
			return {
				list: [

				]
			}
		},
		onReady() {
			this.GetPersonalized()
		},
		methods: {
			GetPersonalized() {
				this.$u.get("personalized", {
					limit: 6
				}).then(res => {
					if (res.code == 200) {

						this.list = res.result
					}
				}).catch(err => {
					console.log(err)
				})

			},
			toListDetail(id) {

				this.$u.route({
					url: "components/song-list-detail",
					params: {
						id
					}
				})

			}
		}
	};
</script>

<style lang="scss" scoped>
	.content {
		padding: 0 32rpx;
		overflow: scroll;



		.title {
			font-size: 48rpx;
			margin-bottom: 10rpx;
		}

		.list {
			display: flex;
			justify-content: flex-start;
			align-items: center;

			&-item {
				width: 240rpx;
				height: 240rpx;
				margin-right: 15rpx;
				display: flex;
				flex-direction: column;
				justify-content: flex-start;
				align-items: center;

				.img {
					width: 100px;
					height: 100px;
					border-radius: 5px;
					align-self: flex-end;
				}

				.name {
					width: 100px;
					height: 40px;
					font-size: 24rpx;
					overflow: hidden;
				}
			}
		}

	}

	.content::-webkit-scrollbar {
		display: none
	}
</style>
