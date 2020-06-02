<template>
	<view class="recommend">
		<view class="recommend-item" v-for="item in recommends">
			<image :src="item.image" />
			<text>{{item.title}}</text>
		</view>
	</view>
</template>

<script>
	export default {
	  name: "RecommendView",
	  props:{
	    recommends:{
	      type : Array,
	      default(){
	        return []
	      }
	    }
	  }
	}
</script>

<style scoped>
	.recommend {
		display: flex;
		text-align: center;
		font-size: 12px;
		width: 100%;
		padding: 20rpx 0px 40rpx 0;
		border-bottom: 20rpx solid #eee;
	}

	.recommend-item {
		display: flex;
		flex-direction: column;
		align-items: center;
		flex: 1;
	}

	.recommend-item image {
		flex: 1;
		width: 140rpx;
		height: 140rpx;
		margin-bottom: 20rpx;
	}
</style>
