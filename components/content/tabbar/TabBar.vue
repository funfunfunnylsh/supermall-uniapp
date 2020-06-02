<template>
	<scroll-view class="tabbar_top" scroll-with-animation scroll-x enable-flex :scroll-into-view="scrollIntoView">
		<view v-for="(item,index) in tabsList" :key="index" class="tab_item" :id="'tabId'+index"
		 :style="tabsWidth">
			<text @click="changeTabs(index)" :class="['tab_text',tabIndex === index ? 'activeColor' : '']">{{item}}</text>
			<view v-show="tabIndex === index" class="tab_line"></view>
		</view>
	</scroll-view>
</template>

<script>
	export default {
		name: 'TabBar',
		props: {
			tabsList: {
				type: Array,
				default () {
					return []
				}
			},
			isTabFixed: {
				type: Boolean,
				default: false
			}
		},
		data() {
			return {
				tabIndex: 0,
				scrollIntoView: "tabId0",
				tabsWidth: {}
			}
		},
		mounted() {
			if (this.isTabFixed && this.tabsList.length <= 5) {
				this.tabsWidth = {
					width: 100 / (this.tabsList.length) + '%'
				}
			}
		},
		methods: {
			changeTabs(index) {
				// 1.改变currentIndex
				this.tabIndex = index;
				this.scrollIntoView = "tabId" + index;
				// 2.发出事件
				this.$emit('itemClick', index)
			}
		}
	}
</script>

<style scoped>
	.tabbar_top {
		width: 750rpx;
		white-space: nowrap;
		display: flex;
		box-shadow: 0 1px 1px rgba(100, 100, 100, .2);
	}

	.tab_item {
		flex: 1;
		display: inline-block;
		text-align: center;
		
	}

	.tab_text {
		color: #aaa;
		font-size: 15px;
		flex: 1;
		line-height: 80rpx;
		padding: 0 40rpx;
	}

	.activeColor {
		color: #DD524D;
	}
	
	.tab_line{
		height: 2px;
		background-color: #DD524D;
		margin: 0px 60rpx;
	}
</style>
