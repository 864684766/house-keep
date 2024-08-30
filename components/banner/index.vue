<template>
	<swiper class="swiper-box" indicator-dots autoplay>
		<swiper-item v-for="(item, index) in props.images" :key="index">
			<view class="swiper-item" @click="clickItemHandle">
				<image :src="item.url" class="swiper-box-item" fade-show show-menu-by-longpress />
			</view>
		</swiper-item>
	</swiper>
</template>

<script setup lang="uts">
	const props = withDefaults(defineProps<{ images ?: { url : string }[] | [] }>(), {
		images: null,
	})

	const clickItemHandle = () => {

	}
</script>

<style scoped lang="scss">
	.swiper-box-item {
		width: 100%;
	}
</style>