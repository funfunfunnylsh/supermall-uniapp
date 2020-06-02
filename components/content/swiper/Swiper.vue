<template>
	<swiper class="swiper" indicator-dots autoplay :interval="5000" :duration="500" circular indicator-active-color="#FF8198">
		<swiper-item v-for="item in swipers" :key="item.id">
			<image :src="item.image"></image>
		</swiper-item>
	</swiper>
</template>

<script>
	export default {
		name: "MySwiper",
		props: {
			swipers: {
				type: Array,
				default () {
					return []
				}
			}
		},
	}
</script>

<style lang="scss">
	.swiper {
		height: 390rpx;

		image {
			width: 750rpx;
			height: 390rpx;
		}
	}
</style>
