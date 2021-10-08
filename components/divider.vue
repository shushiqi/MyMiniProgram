<template>
	<view class="u-divider">
		<view class="u-divider-line" :class="[type ? 'u-divider-line--bordercolor--' + type : '']" :style="[lineStyle]">
		</view>

	</view>
</template>

<script>
	export default {
		name: 'divider',

		computed: {
			lineStyle() {
				let style = {};
				if (String(this.halfWidth).indexOf('%') != -1) style.width = this.halfWidth;
				else style.width = this.halfWidth + 'rpx';
				// borderColor优先级高于type值
				if (this.borderColor) style.borderColor = this.borderColor;
				return style;
			}
		},
	};
</script>

<style lang="scss" scoped>
	.u-divider {
		width: 100%;
		height: 25rpx;
		position: relative;
		text-align: center;
		overflow: hidden;
	}



	.u-divider-line {
		border-right: 1px solid $u-border-color;
		// transform: scale(1, 0.5);
		transform: scale(0.5, 1);
		transform-origin: center;

	}

	.u-divider-text {
		white-space: nowrap;
		padding: 0 16rpx;
		/* #ifndef APP-NVUE */
		display: inline-flex;
		/* #endif */
	}
</style>
