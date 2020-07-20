<template>
	<view>
		<view class="search">
			<view class="search-bar">
				<image src="../../static/search.png" mode="">
					<!-- <label style="margin-left: 10upx;">搜索</label> -->
					<input type="text" confirm-type="search" placeholder="搜索" style="margin-left: 60upx;font-size: 30upx;color: #999999;"></input>
				</image>
			</view>
		</view>
		
		<view class="content" style="margin-bottom: 180upx;">
			<view class="content_text">支持类</view>
			<view class="content_hengb">
				<view class="goods" @click="linhgoods">
					<image src="../../static/logo.png"></image>
					<view class="goods_text">
						单手龙骨产品
					</view>
					<view style="color: #DD524D;text-align: center;padding: 10upx;">
						￥ 2000
					</view>
				</view>
				
				<view class="goods">
					<image src="../../static/logo.png"></image>
					<view class="goods_text">
						单手龙骨产品
					</view>
					<view style="color: #DD524D;text-align: center;padding: 10upx;">
						￥ 2000
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
				bannrelist: {
					0:'../../static/bannre.png'
					// 1:'../../static/bannre.png'
				}
			}
		},
		onLoad() {
	
		},
		methods: {
			linhgoods:function(){
				uni.navigateTo({
					url:"goods/goodsDetails"
				})
			}
		}
	}
</script>

<style>
	page{
		background-color: #f5f5f5;
		width: 100%;
		height: 100%;
	}
	.search {
		color: #808080;
		height: 75upx;
		background-color: #FFFFFF;
		border-radius: 5px;
		width: 720upx;
		margin: 0 auto;
		margin-top: 20upx;
		margin-bottom: 20upx;
		font-size: 30upx;
	}
	.search-bar {
		padding-top: 20upx;
	}
	.search-bar image{
		width: 30upx;height: 30upx;float: left;margin-left: 4%;margin-right: 10upx;margin-top: 4upx;
	}
	.content{
		width: 750upx;
		margin: 10upx auto;
	}
	.content_text{
		font-size: 30upx;
		color: #1e936b;
		margin-bottom: 10upx;
		margin-left: 34upx;
	}
	.content_hengb{
		width: 100%;
	}
	.goods{
		width: 45%;
		font-size: 30upx;
		float: left;
		margin-left: 3%;
		background-color: #FFFFFF;
		border-radius: 10upx;
	}
	.goods image{
		width: 90%;
		height: 320upx;
		margin-left: 5%;
		margin-top: 20upx;
	}
	.goods_text{
		width: 90%;
		margin-left: 5%;
		text-align: center;
	}
</style>
