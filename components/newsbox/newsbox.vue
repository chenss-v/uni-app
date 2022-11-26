<template>
	<view class="newbox">
		<view class="pic">
			<image :src="item.picurl" mode="aspectFill"></image>
		</view>
		<view class="text">
			<view class="title">
				<view class="t">
					{{ item.title }}
				</view>				
			</view>
			<view class="info" v-if="!item.looktime">
				<text>{{ item.author }}</text>
				<text>{{ item.hits }}</text>
			</view>
			<view class="info" v-else>
				<text>浏览时间:{{ item.looktime }}</text>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		name:"newsbox",
		props: {
			item: {
				type: Object,
				default () {
					return {
						title: "组件内默认的标题",
						author: "张三",
						hits: 668,
						picurl: "../../static/images/ceshi.jpg",
						looktime: "2022-11-17 16:40:00"
					}
				}
			}
		},
		data() {
			return {
				
			};
		}
	}
</script>

<style lang="scss">
.newbox{
	display: flex;
	.pic{
		width: 230rpx;
		height: 160rpx;
		image{
			width: 100%;
			height: 100%;
		}
	}
	.text{
		padding-left: 20rpx;
		flex: 1;
		display: flex;
		flex-direction: column;
		justify-content: space-between;
		.title{
			font-size: 38rpx;
			color: #333;
			.t{
				// text-overflow: -o-ellipsis-lastline;
				// overflow: hidden;
				// text-overflow: ellipsis;
				// display: -webkit-box;
				// -webkit-line-clamp: 2;
				// line-clamp: 2;
				// -webkit-box-orient: vertical;
				word-break: break-all;
				text-overflow: ellipsis;
				display: -webkit-box;
				-webkit-box-orient: vertical;
				-webkit-line-clamp: 2; /* 这里是超出几行省略 */
				overflow: hidden;
			}			
		}
		.info{
			font-size: 26rpx;
			color: #999;
			text{
				padding-right: 30rpx;
			}
		}
	}
}
</style>