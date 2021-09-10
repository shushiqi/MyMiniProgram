<template>
	<view class="content">
		<top-layout>
			<image src="" mode=""></image>
			<text v-slot="title"></text>
		</top-layout>

	</view>
</template>

<script>
	import TopLayout from "@/components/layout/top-layout.vue"
	export default {
		components: {
			TopLayout
		}
	}
</script>

<style>
</style>
