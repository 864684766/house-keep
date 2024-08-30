<template>
	<view class="module-nav">
		<uni-grid :column="state.column" :highlight="false" :showBorder="false" :square="false">
			<uni-grid-item v-for="(item, index) in modulesComp" :index="index" :key="index">
				<view class="grid-item-box" @click="clickModuleHandle(item)">
					<uni-icons fontFamily="iconfont" size="25" :color="item.iconColor"> {{item.icon}}</uni-icons>
					<text class="grid-item-box-text">{{item.title}}</text>
					<view v-if="item.activeState" class="grid-dot">
						<uni-badge :text="item.activeText||'特惠'" />
					</view>
				</view>
			</uni-grid-item>
		</uni-grid>
	</view>
</template>

<script setup lang="uts">
	import { computed, defineProps, reactive } from 'vue';
	type ImoduleItem = {
		url : string,
		title : string,
		icon : string,
		activeState : boolean,
		activeText : string,
		iconColor : string
	}
	type Iprops = {
		modules : ImoduleItem[] | any
	}
	const props = withDefaults(defineProps<Iprops>(), {
		modules: []
	})

	const clickModuleHandle = (item : ImoduleItem) => {
		console.log(item.url);
	}

	const state = reactive({ column: 3 })

	const modulesComp = computed(() => {
		return props.modules.map((item : ImoduleItem, idx : number) => {
			let iconColor = ""
			const num = idx % state.column
			switch (num) {
				case 0:
					iconColor = "#4B81F4";
					break;
				case 1:
					iconColor = "#e64340";
					break;
				case 2:
					iconColor = "#60D2B5";
					break;
				default:
					iconColor = "#4B81F4";
			}
			return {
				...item,
				iconColor
			}
		})
	});
</script>

<style lang="scss" scoped>
	@font-face {
		font-family: iconfont;
		src: url('@/static/font/iconfont.ttf');
	}

	.module-nav {
		background: #fff;
		padding: 10rpx;

		.grid-item-box {
			display: flex;
			align-items: center;
			justify-content: center;
			flex-direction: column;
			margin: 40rpx 10rpx 0rpx 0;

			&-text {
				margin-top: 2rpx;
				font-size: 26rpx;
			}

			.grid-dot {
				position: absolute;
				top: 5rpx;
				right: 30rpx;
			}
		}
	}
</style>