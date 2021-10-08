<template>
	<view class="main-content" :class="{column: top}">
		<view class="image" >
			<slot name="img"></slot>
		</view>
		<view class="title">
			<slot name="title"></slot>
		</view>
	</view>
</template>

<script>
	export default {
		name: "TopLayout",
		props: {
			top: {
				type: Boolean,
				default: false
			},
			// img:{
			// 	type:String,
			// 	default:""
			// },
			// title:{
			// 	type:String,
			// 	default:""
			// },
			
		},
		data() {
			return {

			};
		}
	}
</script>

<style lang="scss">
	.main-content {
		width: 100%;
		display: flex;
		justify-content: flex-start;

	}

	.column {
		flex-direction: column;
	}
</style>
