<template>
	<view>
		<view class="top">
			<view class="top_left">
				<view class="top_text" style="font-size: 30upx;">可用积分</view>
				<view class="top_text" style="font-size: 50upx;margin-top: 20upx;">6309</view>
			</view>
		</view>
		
		<view class="content">
			<view class="tab">
				<label class="tab_left" :class="index ? 'tabclass' : ''" @click="tab">收入</label>
				<label class="tab_right" :class="index ? '' : 'tabclass'" @click="tab">支出</label>
			</view>
			
			<view v-if="index">
				<view class="heng">
					<image mode="aspectFit" src="../../../static/integral_icoa.png"></image>
					<view style="float: left;width: 500upx;">
						<view style="font-size: 30upx;">完成订单</view>
						<view style="margin-right: 10upx;color: #888888;font-size: 25upx;margin-top: 10upx;">2020-04-04 18:22:00</view>
					</view>
					<view style="float: left;width: 100upx;">
						<text style="font-size: 30upx;margin-top: 60upx;">+30</text>
					</view>
				</view>
				<view class="heng">
					<image mode="aspectFit" src="../../../static/integral_icoa.png"></image>
					<view style="float: left;width: 500upx;">
						<view style="font-size: 30upx;">完成订单</view>
						<view style="margin-right: 10upx;color: #888888;font-size: 25upx;margin-top: 10upx;">2020-04-04 18:22:00</view>
					</view>
					<view style="float: left;width: 100upx;">
						<text style="font-size: 30upx;margin-top: 60upx;">+30</text>
					</view>
				</view>
			</view>
			
			<view v-else>
				<view class="heng">
					<image mode="aspectFit" src="../../../static/integral_icob.png"></image>
					<view style="float: left;width: 500upx;">
						<view style="font-size: 30upx;">积分总换</view>
						<view style="margin-right: 10upx;color: #888888;font-size: 25upx;margin-top: 10upx;">2020-04-04 18:22:00</view>
					</view>
					<view style="float: left;width: 100upx;">
						<text style="font-size: 30upx;margin-top: 60upx;">+30</text>
					</view>
				</view>
				<view class="heng">
					<image mode="aspectFit" src="../../../static/integral_icob.png"></image>
					<view style="float: left;width: 500upx;">
						<view style="font-size: 30upx;">积分总换</view>
						<view style="margin-right: 10upx;color: #888888;font-size: 25upx;margin-top: 10upx;">2020-04-04 18:22:00</view>
					</view>
					<view style="float: left;width: 100upx;">
						<text style="font-size: 30upx;margin-top: 60upx;">+30</text>
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				title: 'Hello',
				index:true
			}
		},
		onLoad() {

		},
		methods: {
			address(){
				uni.navigateTo({
					url:'./AddressManagement/AddressManagement'
				})
			},
			tab:function(){
				this.index = !this.index;
			}
		}
	}
</script>

<style>
	.tab{
		height: 100upx;
		margin-top: 50upx;
	}
	.tab .tabclass{
		color: #47916e;
		border-bottom: #1AAD19 4upx solid;
	}
	.tab_left{
		color: #888888;
		float: left;
		margin-left: 140upx;
		padding-bottom: 10upx;
	}
	.tab_right{
		color: #888888;
		float: right;
		margin-right: 140upx;
		padding-bottom: 10upx;
	}
	.top{
		height: 400upx;
		background-color: #219975;
	}
	.top .top_left{
		float: left;
		text-align: center;
		margin-top: 15%;
		width: 100%;
	}
	.top .top_left .top_text{
		color: #F1F1F1;
		font-weight:bold;
	}
	.content{
		position: absolute;
		top: 330upx;
		background: #FFFFFF;
		width:100%;
		border-radius:46upx;
	}
	.content .heng{
		border-bottom: #C0C0C0 0.5upx solid;
		height: 120upx;
		float: left;
		margin-bottom: 50upx;
	}
	.content .heng image{
		width: 90upx;
		height: 90upx;
		float: left;
		margin-right: 20upx;
		margin-left: 40upx;
	}
</style>
