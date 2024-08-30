<template>
	<view class="home-page">
		<toolbar :actives="state.actives" />
		<banner :images="state.images" />

		<view class="content">
			<module-nav :modules="state.modules" />
			<welfare :actives="state.actives" />
		</view>
	</view>
</template>

<script setup lang="uts">
	import {
		reactive
	} from 'vue';

	import toolbar from '@/components/toolbar/index.vue'

	import banner from '@/components/banner/index.vue'

	import moduleNav from '@/components/moduleNav/index.vue'

	import welfare from './components/welfare.vue'

	const state = reactive({
		name: "利好",
		images: [
			{
				url: "http://124.71.135.104:8081/images/1.jpg"
			}, {
				url: "http://124.71.135.104:8081/images/2.jpeg"
			}, {
				url: "http://124.71.135.104:8081/images/3.jpeg"
			}, {
				url: "http://124.71.135.104:8081/images/4.jpg"
			}
		],
		modules: [
			{
				url: "",
				title: "数码维修",
				icon: "\ue629",
				activeState: true,
			}, {
				url: "",
				title: "管道维修",
				icon: "\ue622",
				activeState: true,
				activeText: "限时"
			}, {
				url: "",
				title: "保洁服务",
				icon: "\ue71b",
				activeState: false,
				activeText: ""
			}, {
				url: "",
				title: "房屋维修",
				icon: "\ue604",
				activeState: false,
				activeText: ""
			}, {
				url: "",
				title: "安心搬家",
				icon: "\ue64a",
				activeState: false,
				activeText: ""
			}, {
				url: "",
				title: "深度清洗",
				icon: "\ue60e",
				activeState: false,
				activeText: ""
			}
		],
		actives: [
			{
				url: "http://124.71.135.104:8081/images/active/20240830164101.png",
				active_url: "",
				grid_size: 2
			}, {
				url: "http://124.71.135.104:8081/images/active/31.png",
				active_url: "",
				grid_size: 2
			}, {
				url: "http://124.71.135.104:8081/images/active/b305c3f22722f64bbc3ccb89ed237047.jpeg",
				active_url: "",
				grid_size: 1
			}
		]
	})

	const gotoPage = () => {
		uni.navigateTo({
			url: "/pages/category/index"
		})
	}
</script>

<style scoped lang="scss">
	.home-page {
		background: $uni-bg-color-grey;
	}

	.content {
		box-sizing: border-box;
	}

	.logo {
		height: 200rpx;
		width: 200rpx;
		margin-top: 200rpx;
		margin-left: auto;
		margin-right: auto;
		margin-bottom: 50rpx;
	}

	.text-area {
		display: flex;
		justify-content: center;
	}

	.title {
		font-size: 36rpx;
		color: #8f8f94;
	}
</style>