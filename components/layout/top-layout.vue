<template>
	<view class="main-content">
		<view class="image">
			<slot name="img"></slot>
		</view>
		<view class="title">
			<slot name="title"></slot>
		</view>
	</view>
</template>

<script>
	export default {
		name:"TopLayout",
		props: {
			position: {
				type: String,
				default: "left"
			}
		},
		data() {
			return {

			};
		}
	}
</script>

<style lang="scss">
	

	.main-content {
		display: flex;

		justify-content: flex-start;
	}
</style>
