<template>
	<view class="home">
		<my-swiper :swipers="banners"></my-swiper>
		<recommend-view :recommends="recommends"></recommend-view>
		<feature-view></feature-view>
		<tab-bar :tabsList="tabsList" isTabFixed></tab-bar>
		<text>娃哈哈</text>
	</view>
</template>

<script>
	import {
		RECOMMEND,
		BANNER,
		NEW,
		POP,
		SELL,
		BACKTOP_DISTANCE
	} from "common/constant";

	import MySwiper from "../../components/content/swiper/Swiper"
	import RecommendView from "./childCps/RecommendView"
	import FeatureView from "./childCps/FeatureView"
	import TabBar from '../../components/content/tabbar/TabBar'

	export default {
		components: {
			MySwiper,
			RecommendView,
			FeatureView,
			TabBar
		},
		data() {
			return {
				tabsList: ['流行', '新款', '精选'],
				banners: [],
				recommends: [],
				tabsWidth:{}
			}
		},
		onLoad() {
			this.tabsWidth = { width : 100/(this.tabsList.length) + '%'}
			
			// 1.请求多个数据
			this.getMultiData()
			
			
		},
		methods: {
			getMultiData() {
				this.$myRequest({
					method: 'GET',
					url: '/home/multidata'
				}).then(res => {
					console.log(res)
					this.banners = res.data[BANNER].list
					this.recommends = res.data[RECOMMEND].list
				})
			}
			
		}
	}
</script>

<style lang="scss">
	
</style>
