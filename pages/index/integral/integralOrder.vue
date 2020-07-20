<template>
	<view>
		<view class="site">
			<view class="sitename">
				<view style="text-indent:2em;">姓名: 百威师</view>
				<view>联系电话: 15930536620</view>
				<text>收货地址: 广东省广州市海珠区凤凰新村</text>
				<!-- <view>百威师<text class="name">15930536620</text></view> -->
			</view>
			<view class="arrows" @click="linkaddress">
				<image src="../../../static/more.png" mode=""></image>
			</view>
		</view>
		<view style="width: 100%;background-color: #f5f5f5;"></view>
		
		<view class="pitchon" v-for="(items,index) in data_goods" :key="index">
			<view class="pitchon_left">
				<image class="drawing" :src="items.img" mode=""></image>
			</view>
			<view class="pitchon_right">
				<text class="GoodsTitle">商品名称</text>
				<view style="margin-top: 70upx;">
					<text class="discounts" style="float: left;">2000积分</text>
					<!-- <text style="float: right;color: #999999">X 1</text> -->
					<text class="add" style="float: right;" @click="sumupdate(index,'add')">+</text>
					<text class="goods_sum" style="float: right;" type="text">{{items.sum}}</text>
					<text class="subtract" style="float: right;" @click="sumupdate(index,'cut')">-</text>	
				</view>
			</view>
		</view>
		
		<view class="close">
			<view class="twenty">
				合计: <text style="color: #f58895;margin-left: 10upx;">2000积分</text>
			</view>
			
			<view class="forty">
				<button class="btnRed"><label style="padding-bottom: 10upx;">立即兑换</label></button>
			</view>
			
			<view style="clear: both;"></view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				data_goods: [
					{img:'../../../static/goods_ico.png',title: '两用6件（6-14）',class: false,sum:1},
					{img:'../../../static/goods_ico.png',title: '两用6件（6-14）',class: false,sum:1},
					{img:'../../../static/goods_ico.png',title: '两用6件（6-14）',class: false,sum:1}
				],
			}
		},
		methods: {
			sumupdate(index,type){
				if(type == 'add'){
					++this.data_goods[index].sum;
				}else{
					if(this.data_goods[index].sum < 2){
						return
					}
					--this.data_goods[index].sum;
				}
			},
			linkaddress(){
				uni.navigateTo({
					url:'../../PersonalCenter/AddressManagement/AddressManagement'
				})
			}
		}
	}
</script>

<style lang="scss">
	.goods_sum {
		height: 42upx;
		width: 30upx;
		text-align: center;
		background-color: #f5f5f5;
	}
	.add{
		margin-left: 10upx;
	}
	.subtract{
		margin-right: 10upx;
	}
	.close{
		width: 100%;
		height: 110upx;
		position: fixed;
		left: 0;
		bottom: 0;
		background: #FFFFFF;
		text-align: center;
		line-height: 110upx;
		.twenty{
			float: left;
			margin-left: 20upx;
			font-size: 35upx;
		}
		
		.forty{
			float: right;
			width: 37%;
			
			.btnRed{
				width: 240upx;
				height: 80upx;
				background: #eca941;
				color: #FFFFFF;
				margin-top: 16upx;
				border-radius: 50upx;
				font-size: 32upx;
			}
		}
	}
	page{
		background-color: #f5f5f5;
	}
	.discounts{
		color: #f58895;
	}
	.pitchon_left{
		vertical-align: middle;
		width: 30%;
		float: left;
	}
	.drawing{
		float: left;
		width: 180upx;
		height: 170upx;
		margin-left: 20upx;
		vertical-align: middle;
	}
	.pitchon{
		float: left;
		border-radius: 10upx;
		margin-bottom: 20upx;
		height: 200upx;
		width: 100%;
		background: #FFFFFF;
		padding-top: 30upx;
	}
	.pitchon_right{
			float: left;
			width: 65%;
			top: 90upx;
			right: 100upx;
			font-size: 30upx;
	}
	.site{
			float: left;
			width: 100%;
			background: #FFFFFF;
			font-size: 32upx;
			padding-top: 24upx;
			padding-bottom: 24upx;
			margin-bottom: 24upx;
			.sitename{
				width: 86%;
				letter-spacing:2upx;
				line-height: 60upx;
				padding-left: 4%;
				float: left;
				.name{
					margin-left: 40upx;
				}
			}
			.arrows{
				width: 10%;
				height: 156upx;
				text-align: center;
				line-height: 156upx;
				top: 0.5%;
				right: 2%;
				font-size: 50upx;
				float: left;
				image{
					width: 22upx;
					height: 38upx;
				}
			}
		}
</style>
