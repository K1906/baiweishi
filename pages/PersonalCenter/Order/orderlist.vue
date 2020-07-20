<template>
	<view>
		<view class="show" :style="{display:show?'':'none'}">
			<view class="back">
				<view class="back_text">快递公司: 圆通速递</view>
				<view class="back_text">订单号: 123465789</view>
				<view class="back_but" @click="shutdownorser">
					完成
				</view>
			</view>
		</view>
		<view class="tab" style="background-color: #FFFFFF;height: 76upx;">
			<label class="tab_left" :class="index ? 'tabclass':''" @click="tab(true)">产品订单</label>
			<label class="tab_right" :class="index ? '':'tabclass'" @click="tab(false)">积分订单</label>
		</view>
		
		<view v-if="index">
			<view class="order" style="background-color: #FFFFFF;">
				<view class="order_sn">
					<label>订单编号: 123456789</label>
				</view>
				<view class="order_goods">
					<image src="../../../static/logo.png" mode=""></image>
					<view class="order_goods_in">
						<view style="font-size: 30upx;">商品名称商品名称商品名称商品名称</view>
						<view style="font-size: 30upx;margin-top: 12upx;color: #999999;">规格:红色</view>
					</view>
					
					<view class="order_goods_right">
						<view style="font-size: 30upx;color: #DD524D;">￥2002</view>
						<view style="font-size: 30upx;margin-top: 50upx;color: #999999;margin-left: 60upx;">x 1</view>
					</view>
				</view>
				
				<view class="order_total">
					<label style="float: left;margin-left: 20upx;margin-top: 10upx;font-size: 30upx;">合计:<label style="color: #DD524D;margin-left: 10upx;">￥2002</label></label>
						<label class="button" @click="vieworsersn">查看单号</label>
				</view>
			</view>
			
			<view class="order"  style="background-color: #FFFFFF;">
				<view class="order_sn">
					<label>订单编号: 123456789</label>
				</view>
				<view class="order_goods">
					<image src="../../../static/logo.png" mode=""></image>
					<view class="order_goods_in">
						<view style="font-size: 30upx;">商品名称商品名称商品名称商品名称</view>
						<view style="font-size: 30upx;margin-top: 12upx;color: #999999;">规格:红色</view>
					</view>
					
					<view class="order_goods_right">
						<view style="font-size: 30upx;color: #DD524D;">￥2002</view>
						<view style="font-size: 30upx;margin-top: 50upx;color: #999999;margin-left: 60upx;">x 1</view>
					</view>
				</view>
				
				<view class="order_total">
					<label style="float: left;margin-left: 20upx;margin-top: 10upx;font-size: 30upx;">合计:<label style="color: #DD524D;margin-left: 10upx;">￥2002</label></label>
						<label class="button" @click="vieworsersn">查看单号</label>
				</view>
			</view>
		</view>
		
		<view v-else>
			<view class="order" style="background-color: #FFFFFF;">
				<view class="order_sn">
					<label>订单编号: 123456789</label>
				</view>
				<view class="order_goods">
					<image src="../../../static/logo.png" mode=""></image>
					<view class="order_goods_in">
						<view style="font-size: 30upx;">商品名称商品名称商品名称商品名称</view>
						<view style="font-size: 30upx;margin-top: 12upx;color: #999999;">规格:红色</view>
					</view>
					
					<view class="order_goods_right">
						<view style="font-size: 30upx;color: #DD524D;">2002积分</view>
						<view style="font-size: 30upx;margin-top: 50upx;color: #999999;margin-left: 60upx;">x 1</view>
					</view>
				</view>
				
				<view class="order_total">
					<label style="float: left;margin-left: 20upx;margin-top: 10upx;font-size: 30upx;">合计:<label style="color: #DD524D;margin-left: 10upx;">2002积分</label></label>
						<label class="button" @click="vieworsersn">查看单号</label>
				</view>
			</view>
			
			<view class="order"  style="background-color: #FFFFFF;"> 
				<view class="order_sn">
					<label>订单编号: 123456789</label>
				</view>
				<view class="order_goods">
					<image src="../../../static/logo.png" mode=""></image>
					<view class="order_goods_in">
						<view style="font-size: 30upx;">商品名称商品名称商品名称商品名称</view>
						<view style="font-size: 30upx;margin-top: 12upx;color: #999999;">规格:红色</view>
					</view>
					
					<view class="order_goods_right">
						<view style="font-size: 30upx;color: #DD524D;">2002积分</view>
						<view style="font-size: 30upx;margin-top: 50upx;color: #999999;margin-left: 60upx;">x 1</view>
					</view>
				</view>
				
				<view class="order_total">
					<label style="float: left;margin-left: 20upx;margin-top: 10upx;font-size: 30upx;">合计:<label style="color: #DD524D;margin-left: 10upx;">2002积分</label></label>
						<label class="button" @click="vieworsersn">查看单号</label>
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
				index:true,
				show:false
			}
		},
		onLoad() {

		},
		methods: {
			vieworsersn:function(){
				this.show = true
			},
			shutdownorser:function(){
				this.show = false
			},
			address(){
				uni.navigateTo({
					url:'./AddressManagement/AddressManagement'
				})
			},
			tab(index){
				this.index = index;
				console.log(this.index)
			}
		}
	}
</script>

<style>
	page{
		background-color: #f5f5f5;
	}
	.back_but{
		text-align: center;
		width: 170upx;
		height: 50upx;
		background-color: #F0AD4E;
		border-radius: 5upx;
		color: #FFFFFF;
		margin: auto;
		font-size: 30upx;
		margin-top: 30upx;padding-top: 10upx;
		padding-bottom: 4upx;
	}
	.show{
		width: 100%;
		height: 100%;
		background-color: rgba(0,0,0,0.1);
		position: absolute;
		z-index: 999;
	}
	.back{
		background-color: #FFFFFF;
		width: 450upx;
		border-radius: 20upx;
		height: 280upx;
		position: absolute;
		margin: 50% 20%;
	}
	.back_text{
		font-size: 30upx;
		padding-top: 32upx;
		text-align: center;
	}
	.order{
		border-top: #E5E5E5 20upx solid;
		width: 100%;
		float: left;
	}
	.order .order_sn{
		border-bottom: #C0C0C0 0.5upx solid;
		color: #999999;
		font-size: 30upx;
		margin-top: 20upx;
		padding-bottom: 20upx;
	}
	.order .order_sn label{
		margin: 30upx;
	}
	.order_goods{
		float: left;
		width: 100%;
	}
	.order_goods image{
		margin: 20upx 30upx;
		float: left;
		width: 140upx;
		height: 140upx;
	}
	.order_goods_in{
		float: left;
		width: 50%;
		margin-top: 20upx;
	}
	.order_goods_right{
		float: left;
		margin-top: 20upx;
		margin-left: 3%;
		width: 18%;
	}
	.order_total{
		margin-left: 10upx;
		margin-bottom: 30upx;
		float: left;
		width: 100%;
	}
	.button{
		color: #FFFFFF;margin-right: 10upx;float: right;width: 200upx;height: 60upx;border-radius: 10upx;
		text-align: center;
		font-size: 32upx;
		padding-top: 14upx;
		background-color: #219975;
		margin-right: 25upx;
	}
	.tab{
		font-size: 30upx;
	}
	.tab .tabclass{
		color: #219975;
		border-bottom: #219975 4upx solid;
		padding: 16upx;
	}
	
	.tab_left{
		color: #888888;
		float: left;
		margin-left: 140upx;
		padding-bottom: 10upx;
		padding: 16upx;
	}
	.tab_right{
		color: #888888;
		float: right;
		margin-right: 140upx;
		padding-bottom: 10upx;
		padding: 16upx;
	}
</style>
