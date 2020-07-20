<template>
	<view>
		
		<view class="search" @click="linksearch">
			<view class="search-bar">
				<image src="../../static/search.png" mode="" style="width: 26upx;height: 26upx;">
					<label style="margin-left: 10upx;">搜索</label>
				</image>
			</view>
		</view>
		
		<!-- 轮播 -->
		<view class="banner">
			<swiper class="swiper" :indicator-dots="true" :autoplay="true" circular="true" indicator-active-color="#8c8c8c"
			 indicator-color="#ffffff" style="width: 100%;height: 380upx;">
				<swiper-item v-for="(item, key) in bannrelist" :key="key">
					<view class="swiper-item">
						<image :src="item" mode="widthfix"></image>
					</view>
				</swiper-item>
			</swiper>
		</view>
		
		<view class="content">
			<view class="content_text">百威师产品</view>
			<view class="content_heng">
				<view class="goods_class"  @click="linhgoods">
					<image src="../../static/logo.png"></image>
					<view style="text-align: center;font-size: 30upx;">产品</view>
				</view>
				<view class="goods_class"  @click="linhgoods">
					<image src="../../static/logo.png"></image>
					<view style="text-align: center;font-size: 30upx;">产品</view>
				</view>
				<view class="goods_class"  @click="linhgoods">
					<image src="../../static/logo.png"></image>
					<view style="text-align: center;font-size: 30upx;">产品</view>
				</view>
			</view>
			
			<view class="content_heng">
				<view class="goods_class"  @click="linhgoods">
					<image src="../../static/logo.png"></image>
					<view style="text-align: center;font-size: 30upx;">产品</view>
				</view>
				<view class="goods_class"  @click="linhgoods">
					<image src="../../static/logo.png"></image>
					<view style="text-align: center;font-size: 30upx;">产品</view>
				</view>
				<view class="goods_class"  @click="linhgoods">
					<image src="../../static/logo.png"></image>
					<view style="text-align: center;font-size: 30upx;">产品</view>
				</view>
			</view>
			
			<view class="content_heng">
				<view class="goods_class" @click="linhgoods">
					<image src="../../static/logo.png"></image>
					<view style="text-align: center;font-size: 30upx;">产品</view>
				</view>
				<view class="goods_class" @click="linhgoods">
					<image src="../../static/logo.png"></image>
					<view style="text-align: center;font-size: 30upx;">产品</view>
				</view>
				<view class="goods_class" @click="linhgoods">
					<image src="../../static/logo.png"></image>
					<view style="text-align: center;font-size: 30upx;">产品</view>
				</view>
			</view>
		</view>
		
		<view class="content">
			<view class="content_text">其它产品</view>
			<view class="content_heng">
				<view class="goods_class"  @click="linhgoods">
					<image src="../../static/logo.png"></image>
					<view style="text-align: center;font-size: 30upx;">类别产品</view>
				</view>
				<view class="goods_class"  @click="linhgoods">
					<image src="../../static/logo.png"></image>
					<view style="text-align: center;font-size: 30upx;">类别产品</view>
				</view>
				<view class="goods_class"  @click="linhgoods">
					<image src="../../static/logo.png"></image>
					<view style="text-align: center;font-size: 30upx;">类别产品</view>
				</view>
			</view>
			
			<view class="content_heng">
				<view class="goods_class">
					<image src="../../static/logo.png"></image>
					<view style="text-align: center;font-size: 30upx;">类别产品</view>
				</view>
				<view class="goods_class">
					<image src="../../static/logo.png"></image>
					<view style="text-align: center;font-size: 30upx;">类别产品</view>
				</view>
				<view class="goods_class">
					<image src="../../static/logo.png"></image>
					<view style="text-align: center;font-size: 30upx;">类别产品</view>
				</view>
			</view>
			
			<view class="content_heng">
				<view class="goods_class">
					<image src="../../static/logo.png"></image>
					<view style="text-align: center;font-size: 30upx;">类别产品</view>
				</view>
				<view class="goods_class">
					<image src="../../static/logo.png"></image>
					<view style="text-align: center;font-size: 30upx;">类别产品</view>
				</view>
				<view class="goods_class">
					<image src="../../static/logo.png"></image>
					<view style="text-align: center;font-size: 30upx;">类别产品</view>
				</view>
			</view>
		</view>
		
		<view class="content" style="margin-bottom: 180upx;">
			<view class="content_text">积分产品</view>
			<view class="content_hengb">
				<view class="goods" @click="linhintgoods">
					<image src="../../static/logo.png"></image>
					<view class="goods_text">
						积分产品名称单手龙骨20-PPP单手龙骨
					</view>
					<view style="color: #DD524D;text-align: center;padding: 10upx;">
						2000积分
					</view>
				</view>
				
				<view class="goods" @click="linhintgoods">
					<image src="../../static/logo.png"></image>
					<view class="goods_text">
						积分产品名称单手龙骨20-PPP单手龙骨
					</view>
					<view style="color: #DD524D;text-align: center;padding: 10upx;">
						2000积分
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
			linksearch(){
				uni.navigateTo({
					url:'search'
				})
			},
			linhgoods(){
				uni.navigateTo({
					url:'classinnerpage'
				})
			},
			linhintgoods(){
				uni.navigateTo({
					url:'integral/goods_dateil'
				})
			}
		}
	}
</script>

<style>
	.goods{
		width: 47%;
		font-size: 30upx;
		float: left;
		margin-left: 2%;
		background-color: #FFFFFF;
		border-radius: 10upx;
	}
	.goods image{
		width: 90%;
		height: 250upx;
		margin-left: 5%;
		margin-top: 20upx;
	}
	.goods_text{
		width: 90%;
		margin-left: 5%;
	}
	.content_hengb{
		width: 100%;
		height: 350upx;
	}
	.content{
		width: 700upx;
		margin: 10upx auto;
	}
	.content_text{
		font-size: 30upx;
		color: #1e936b;
		margin-bottom: 10upx;
		margin-left: 10upx;
		margin-top: 20upx;
	}
	.content_heng{
		width: 100%;
		height: 260upx;
	}
	.goods_class{
		width: 33.3%;
		float: left;
	}
	.goods_class image{
		width: 90%;
		height: 200upx;
		margin-left: 5%;
	}
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
		width: 686upx;
		margin: 0 auto;
		margin-top: 20upx;
		margin-bottom: 20upx;
		font-size: 30upx;
	}
	.search-bar {
		text-align: center;
		padding-top: 20upx;
	}
	.banner {
	}

	.swiper-item image {
		width: 100%;
		height: 380upx;
	}
	
	.text {
		height: 70upx;
		line-height: 70upx;
	}
	
</style>
