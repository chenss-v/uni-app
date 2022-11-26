<template>
	<view class="history">
		<view class="top">
			<image src="../../static/images/history.png" mode=""></image>
			<view class="text">浏览历史</view>
		</view>
		
		<view class="content">
			<view class="row" v-for="item in listArr">
				<newsbox :item="item" @click.native="goDetail(item)"></newsbox>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				listArr: []
			}
		},
		onLoad() {
			this.getData()
		},
		methods: {
			goDetail(item) {
				uni.navigateTo({
					url: `../detail/detail?cid=${item.classid}&id=${item.id}`
				})
			},
			getData() {
				let hisArr = uni.getStorageSync("historyArr") || []
				this.listArr = hisArr
				console.log(this.listArr)
			}
			
		}
	}
</script>

<style lang="scss">
.top{
	padding: 50rpx 0;
	background-color: #F8F8F8;
	color: #555;
	display: flex;
	flex-direction: column;
	justify-content: center;
	align-items: center;
	image{
		width: 150rpx;
		height: 150rpx;
	}
	.text{
		font-size: 30rpx;
		padding-top: 20rpx;
	}
}
.content{
		padding: 30rpx;
		.row{
			border-bottom: 1px dotted #efefef;
			padding: 20px 0;
		}
	}
</style>
