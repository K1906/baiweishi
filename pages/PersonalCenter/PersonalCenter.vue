<template>
	<view>
		<view class="top">
			<view class="top_left">
				<view class="top_text" style="font-size: 60upx;">Emma Wong</view>
				<view class="top_text" style="font-size: 30upx;">159****6309</view>
			</view>
			
			<view class="top_right">
				<image mode="aspectFit" src="../../static/logo.png"></image>
			</view>
		</view>
		
		<view class="content">
			<view class="heng" style="margin-top: 100upx;" @click="jumporder">
				<image mode="aspectFit" src="../../static/order_ico.png"></image>
				<text style="float: left;font-size: 30upx;">我的订单</text>
				<text style="float: right;margin-right: 10upx;">></text>
			</view>
			
			<view class="heng" @click="integral">
				<image mode="aspectFit" src="../../static/integral_ico.png"></image>
				<text style="float: left;font-size: 30upx;">我的积分</text>
				<text style="float: right;margin-right: 10upx;">></text>
			</view>
			
			<view class="heng" @click="address">
				<image mode="aspectFit" src="../../static/position_ico.png"></image>
				<text style="float: left;font-size: 30upx;">我的地址</text>
				<text style="float: right;margin-right: 10upx;">></text>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				title: 'Hello'
			}
		},
		onLoad() {

		},
		methods: {
			jumporder:function(){
				uni.navigateTo({
					url:'Order/orderlist'
				})
			},
			address:function(){
				uni.navigateTo({
					url:'AddressManagement/AddressManagement'
				})
			},
			integral:function(){
				uni.navigateTo({
					url:'integral/integral'
				})
			}
		}
	}
</script>

<style>
	.top{
		height: 400upx;
		background-color: #219975;
	}
	.top .top_left{
		float: left;
		width: 70%;
		margin-top: 15%;
	}
	.top .top_left .top_text{
		color: #F1F1F1;
		font-weight:bold;
		margin-left: 10%;
	}
	.top .top_right{
		
		float: left;
		width: 30%;
		margin-top: 15%;
	}
	.top .top_right image{
		border-radius: 100upx;
		border: #FFFFFF solid 4upx;
		width: 70%;
		height: 150upx;
	}
	.content{
		position: absolute;
		top: 330upx;
		background: #FFFFFF;
		width:100%;
		border-radius:46upx;
	}
	.content .heng{
		width: 90%;
		margin-left: 20upx;
		height: 60upx;
		float: left;
		margin-bottom: 50upx;
	}
	.content .heng image{
		width: 50upx;
		height: 50upx;
		float: left;
		margin-right: 20upx;
	}
</style>
