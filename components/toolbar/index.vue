<template>
	<view class="tool-bar">
		<view class="address">
			<text class="address-name">{{state.address}}</text>
			<uni-icons fontFamily="iconfont" size="16"> {{'\ue630'}}</uni-icons>
		</view>
		<view class="search">
			<uni-icons type="search" size="16" color="#999"></uni-icons>
			<input class="search-context" type="text" v-model="state.severContext" placeholder="请输入需要的服务" />
		</view>
	</view>
</template>

<script setup lang="uts">
	import { reactive } from 'vue';
	const state = reactive({
		address: "北京",
		severContext: ""
	})
</script>

<style scoped lang="scss">
	@font-face {
		font-family: iconfont;
		src: url('@/static/font/iconfont.ttf');
	}

	.tool-bar {
		display: flex;
		padding: 8rpx 35rpx;
		background: $uni-primary-theme;
		box-sizing: border-box;

		.address {
			background: #fff;
			padding: 12rpx 10rpx;
			border-radius: 50rpx 0 0 50rpx;
			width: 22%;
			border-right: 2rpx solid $uni-border-color;
			display: flex;
			align-items: center;
			text-align: center;

			.address-name {
				text-overflow: ellipsis;
				white-space: nowrap;
				overflow: hidden;
				display: block;
				width: 100%;
			}
		}

		.search {
			padding: 5rpx 10rpx;
			background: #fff;
			display: flex;
			align-items: center;
			border-radius: 0 50rpx 50rpx 0;
			flex: 4;

			.search-context {
				margin-left: 5rpx;
				width: 100%;
			}
		}
	}
</style>