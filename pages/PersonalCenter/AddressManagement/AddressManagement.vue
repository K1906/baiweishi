<template>
	<view class="wrap">
		<view class="title">
			<text class="title_text">我的地址</text>
			<text class="addclass" @click="linh_add">添加</text>
		</view>
		
		<view class="am">
			<view class="am-li index-box bgcon">
				<view class="am-bar">
					<view class="content">
						<view class="am-row">
							收货人: <text style="margin-left: 20upx;">百威师</text>  <text class="moren">默认</text></image>
							<text style="float: right;">15766073577</text>
						</view>
						<view class="am-row">
							收货地址: <text style="margin-left: 20upx;">广东省广州市海珠区凤凰新村</text>
						</view>
					</view>
				</view>
				
				<view class="am-con">
					<view class="right_com">
						<text class="class">
						</text>
						<text class="text" @click="linh_update">
							编辑
						</text>
					</view>
				</view>
			</view>
		</view>
		
		<view class="am">
			<view class="am-li index-box bgcon">
				<view class="am-bar">
					<view class="content">
						<view class="am-row">
							收货人: <text style="margin-left: 20upx;">百威师</text> </image>
							<text style="float: right;">15766073577</text>
						</view>
						<view class="am-row">
							收货地址: <text style="margin-left: 20upx;">广东省广州市海珠区凤凰新村</text>
						</view>
					</view>
				</view>
				
				<view class="am-con">
					<view class="right_com">
						<text class="class">
						</text>
						<text class="text" @click="linh_update">
							编辑
						</text>
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		components: {
		},
		
		data() {
			return {
			};
		},
		
		onLoad: function () {
		},
		
		methods: {
			linh_add: function (e) {
				uni.navigateTo({
					url:'addAddress'
				})
			},
			linh_update: function (e) {
				uni.navigateTo({
					url:'addAddress?id=1'
				})
			}
		},
	}
</script>

<style lang="less">
	page {
		background: #f5f5f5;
	}
	.title{
		width: 100%;height: 100upx;background-color: #FFFFFF;text-align: center;font-size: 30upx;
	}
	.title .title_text{
		float: left;
		margin-left: 41%;
		padding-top: 30upx;
	}
	.addclass{
		right: 0;
		color:#219975;
		float: right;
		padding-top: 30upx;
		margin-right: 36upx;
	}
	.length{
		color: #606266;
		font-size: 30upx;
		margin-top: 50%;
		text-align: center;
	}
	.content{
		margin-left: 20upx;
	}
	.am {
		border-top: 1px solid #f2f2f2;
		font-size: 26upx;
		width: 100%;
		margin-left: 10rpx;
		background-color: #FFFFFF;
		float: left;
		margin-top: 30upx;
		letter-spacing:2upx
	}
	.moren{
		color: #ed0b27;background-color: #fbfad9;width: 20upx;height: 10upx;margin-left: 20upx;padding: 0upx 12upx;
	}


	.am-checked {
		display: flex;
		align-items: center;

		image {
			width: 24upx;
			height: 24upx;
			margin-right: 10upx;
		}
	}

	.am-row {
		margin-bottom: 10upx;
		margin-right: 48upx;
	}
	.am-row image{
		width: 10upx;
		height: 5upx;
	}

	.am-bar {
		padding: 35upx 0 20upx;
		border-bottom: 0.5upx solid #f2f2f2;
		width: 80%;
		float: left;
	}

	.am-con {
		font-size: 26upx;
		width: 20%;
		float: left;
		.content {
			display: flex;
			justify-content: space-between;
		}
	}

	.am-edit {
		display: flex;
		align-items: center;

		image {
			width: 26upx;
			height: 26upx;
			margin-right: 10upx;
		}
	}

	.am-delete {
		display: flex;
		align-items: center;
		margin-left: 40upx;

		image {
			width: 29upx;
			height: 29upx;
			margin-right: 10upx;
		}
	}

	.am-con-right {
		display: flex;
		justify-content: space-between;
		align-items: center;
		height: 90upx;
	}
	.right_com .class{
		height: 55upx;border: #C0C0C0 0.3upx solid;float: left;margin-top: 40upx;
	}
	.right_com .text{
		margin-left: 40upx;font-size: 30upx;color: #219975;margin-top: 50upx;float: left;
	}
</style>
