<template>
	<view class="welfare">
		<view class="welfare-title">
			<text class="title-left title-tag">每日特价</text>
			<view class="btn-more">
				<text>更多</text>
				<uni-icons type="right" size="16"></uni-icons>
			</view>
		</view>
		<view v-show="active_two_list?.length" class="active_two">
			<image v-for="(item,index) in active_two_list" :key="index" :src="item.url" @click="getActiveInfo(item)"
				lazy-load class="active-img" mode="widthFix" />
		</view>
		<view v-show="active_one?.url" class="active_one">
			<image :src="active_one.url" @click="getActiveInfo(active_one)" lazy-load class="active-img" />
		</view>

		<view v-show="active_three_list?.length" class="active_three">
			<image v-for="(item,index) in active_three_list" :key="index" :src="item.url" @click="getActiveInfo(item)"
				lazy-load class="active-img" />
		</view>
	</view>
</template>

<script setup lang="uts">
	import { computed } from 'vue';
	type IactiveItem = {
		url : string,
		active_url : string,
		grid_size : number
	}
	const props = withDefaults(defineProps<{
		actives : IactiveItem[] | any
	}>(), {
		actives: []
	})

	const active_one = computed(() => {
		return props.actives.find((active : IactiveItem) => active.grid_size === 1)
	})

	const active_two_list = computed(() => {
		return props.actives.filter((active : IactiveItem) => active.grid_size === 2)
	})

	const active_three_list = computed(() => {
		return props.actives.filter((active : IactiveItem) => active.grid_size === 3)
	})

	const getActiveInfo = (active : IactiveItem) => {
		console.log(active.url);
	}
</script>

<style scoped lang="scss">
	.welfare {
		background: #fff;
		margin-top: 15rpx;
		padding: 0 10rpx;

		&-title {
			display: flex;
			justify-content: space-between;
			padding: 15rpx 10rpx 0 10rpx;
			font-size: 30rpx;
		}

		.active_one {
			margin-top: 30rpx;
			height: 200rpx;

			:deep(.active-img) {
				display: block;
				width: 100%;
				height: 100%;
				border-radius: 20rpx;
			}
		}

		.active_three {
			margin-top: 30rpx;
			display: flex;
			align-items: center;

			:deep(.active-img) {
				display: block;
				width: 100%;
				border-radius: 20rpx;
			}
		}

		.active_two {
			margin-top: 30rpx;
			display: flex;
			align-items: center;

			:deep(.active-img) {
				display: block;
				width: 100%;
				border-radius: 20rpx;
			}
		}
	}
</style>