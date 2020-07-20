<template>
	<view>
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
			<view class="pd-desc-detail">
				五金梅花开口两用扳手套餐
			</view>
			<view class="pd-desc-info">
				<view class="pd-desc-price">
						<label style="color: #8c8c8c;">价格: </label><label style="margin-left: 10upx;color: #ed2c44;">￥20.5起</label>
				</view>
				<view class="pd-desc-sale">
					月销2300笔
				</view>
			</view>
		</view>
		
		<view style="width: 100%;height: 20upx;background-color: #f5f5f5;"></view>
		
		<view class="content">
			<view class="select"  @click="toggleSpec">
				<view class="select_text">选择 <label style="color: #9f9f9f;margin-left: 10upx;">已选：两用6件</label></view>
				<image src="../../../static/more.png"></image>
			</view>
			<view class="goods_class">
				<image src="../../../static/goods_ico.png"></image>
				<image src="../../../static/goods_ico.png"></image>
				<image src="../../../static/goods_ico.png"></image>
				<image src="../../../static/goods_ico.png"></image>
				<label class="goods_class_text">共4中分类可选</label>
			</view>
		</view>
		
		<view style="width: 100%;height: 20upx;background-color: #f5f5f5;"></view>
		
		<view class="content">
			<view class="select"  @click="toggleData">
				<view class="select_text">参数 <label style="color: #999999;margin-left: 10upx;">品牌/型号...</label></view>
				<image src="../../../static/more.png"></image>
			</view>
		</view>
		
		<view class="content_back">
			<view class="title">
				<image src="../../../static/icon_green.png"></image>
				<label style="margin: 0 20upx;">产品详情介绍</label>
				<image src="../../../static/icon_green.png"></image>
			</view>
		</view>
		
		<view style="width: 100%;">
			<uParse :content="getgroupdata"></uParse>
		</view>
		
		<!-- 底部栏 -->
		<view class="purchasing-foot">
			
			<view class="purchasing-path" @click="linhindex">
					<image src="../../../static/icon_home.png" mode=""></image>
					<view style="text-align: center;">商城</view>
			</view>
			
			<view class="purchasing-path" @click="stores">
					<image src="../../../static/icon_stop.png" mode=""></image>
					<view style="text-align: center;">店铺</view>
			</view>
		
			<view class="purchasing-button1"  @click="toggleSpec">
				<view class="purchasing-dl">
						立即购买
				</view>
			</view>
		
		
			<view class="purchasing-button2"  @click="toggleSpec">
				<view class="purchasing-dl">
						加入购物车
				</view>
			</view>
		
		</view>
		<!-- 规格-模态层弹窗 -->
		<view class="popup spec" :class="specClass" @touchmove.stop.prevent="stopPrevent" >
			<!-- 参数遮罩层 -->
			<view class="mask"  @click="toggleSpec"></view>
			<view class="layer attr-content">
				<view class="layer_goods">
					<image src="../../../static/goods_ico.png" mode=""></image>
					<view class="right_info">
						<view style="color: #DD524D;margin-top: 20upx;">
							￥20.5起
						</view>
						<view style="color: #808080;margin-top: 20upx;">
							已选:两用6件（6-14）
						</view>
					</view>
				</view>
				
				<view style="width: 100%;padding: 30upx;float: left;">分类</view>
				<view style="width: 100%;margin-bottom: 20upx;float: left;">
					<view :class="items.class ? 'layer_spec_class':'layer_spec'" v-for="(items,index) in data_goods" :key="index"  @click="spec(index)">
						<image :src="items.img" style="width: 50upx;height: 50upx;float: left;margin-right: 10upx;"></image> {{items.title}}
					</view>
				</view>
				
				<view class="tc-num">
					<view class="content">
						<view style="float: left;">购买数量</view>
						<view class="computed">
							<view class="reduce" @click="computed(false)">
								-
							</view>
							<view class="total">
								{{num}}
							</view>
							<view class="add" @click="computed(true)">
								+
							</view>
						</view>
					</view>
				</view>
				
				<view @click="addcart" class="but" style="margin-top:50upx;float: left;"><label>加入购物车</label></view>
			</view>
		</view>
		
		<!-- 参数-模态层弹窗 -->
		<view class="popup spec" :class="dataClass" @touchmove.stop.prevent="stopPrevent" @click="toggleData">
			<!-- 参数遮罩层 -->
			<view class="mask"></view>
			<view class="layer attr-content">
				<view style="text-align: center;margin: 20upx 0;border-bottom: #C0C0C0 solid 0.5upx;padding: 20upx 0 30upx 0;"><label>产品参数</label></view>
				<view class="layer_heng">
					<view><label class="layer_text">品牌:</label><label>绿林</label></view>
					<view style="margin-top: 10upx;"><label class="layer_text">类型:</label><label>扳手类</label></view>
				</view>
				<view class="layer_heng">
					<view><label class="layer_text">货号:</label><label>MS4554</label></view>
					<view style="margin-top: 10upx;"><label class="layer_text">型号:</label><label>帆布宝扳手</label></view>
				</view>
				
				<view class="layer_heng">
					<view><label class="layer_text">规格:</label><label>19-21-66</label></view>
					<view style="margin-top: 10upx;"><label class="layer_text">材质:</label><label>明矾合金</label></view>
				</view>
				
				<view class="layer_heng">
					<view><label class="layer_text">制式:</label><label>公制</label></view>
					<view style="margin-top: 10upx;"><label class="layer_text">质量:</label><label>2.3GK</label></view>
				</view>
				
				
				<view class="but" @click="toggleData" style="margin-top:100upx;"><label>完成</label></view>
			</view>
		</view>
	</view>
</template>

<script>
	import uParse from '../../../components/uParse/src/wxParse.vue'
	export default {
		components: {
			uParse
		},
		data() {
			return {
				data_goods: [
					{img:'../../../static/goods_ico.png',title: '两用6件（6-14）',class: true},
					{img:'../../../static/goods_ico.png',title: '两用6件（6-14）',class: false},
					{img:'../../../static/goods_ico.png',title: '两用6件（6-14）',class: false},
					{img:'../../../static/goods_ico.png',title: '两用6件（6-14）',class: false},
					{img:'../../../static/goods_ico.png',title: '两用6件（6-14）',class: false},
					{img:'../../../static/goods_ico.png',title: '两用6件（6-14）',class: false}
				],
				num: 1,
				specClass: 'none',
				dataClass: 'none',
				title: 'Hello',
				getgroupdata:'<img src="http://mtq.juechaowu.com/ueditor/php/upload/image/20190929/1569801166927406.jpg">',
				bannrelist: {
					0:'../../../static/bannre.png',
					1:'../../../static/bannre.png'
				}
			}
		},
		onLoad() {
			console.log(this.data_goods)
		},
		methods: {
			linhindex(){
				uni.switchTab({
					url:'../index'
				})
			},
			addcart:function(){
				this.specClass = 'none';
				this.dataClass = 'none';
				uni.navigateTo({
					url:'shoppingcart'
				})
			},
			//数量
			computed(temp) {
				var that = this;
				if (temp) {
					that.num += 1;
					
				} else {
					if (that.num <= 1) {
						return
					} else {
						that.num -= 1;
					}
				}
			},
			spec(index){
				for (var i=0;this.data_goods.length>i;i++) {
					this.data_goods[i].class = false;
				}
				this.data_goods[index].class = true;
			},
			toggleSpec() {
				if(this.specClass === 'show'){
					this.specClass = 'hide';
					setTimeout(() => {
						this.specClass = 'none';
					}, 250);
				}else if(this.specClass === 'none'){
					this.specClass = 'show';
				}
			},
			toggleData() {
				if(this.dataClass === 'show'){
					this.dataClass = 'hide';
					setTimeout(() => {
						this.dataClass = 'none';
					}, 250);
				}else if(this.dataClass === 'none'){
					this.dataClass = 'show';
				}
			},
			stopPrevent(){},
			stores:function(){
				uni.navigateTo({
					url:'stores'
				})
			}
		}
	}
</script>

<style lang='scss'>
	.computed {
		display: flex;
		right: 0;
		height: 50upx;
		margin-left: 55%;
	
		.reduce {
			width: 60upx;
			height: 50upx;
			text-align: center;
			line-height: 50upx;
			font-size: 28upx;
		}
	
		.total {
			width: 60upx;
			height: 50upx;
			background-color: #f5f5f5;
			text-align: center;
			line-height: 50upx;
			font-size: 28upx;
		}
	
		.add {
			width: 60upx;
			height: 50upx;
			text-align: center;
			line-height: 50upx;
			font-size: 28upx;
		}
	}
	.tc-num {
		padding: 10upx;
		font-size: 30upx;
		float: left;
		width: 100%;
		.content {
			margin-bottom: 25upx;
			display: flex;
			align-items: center;
		}
	}
	/*  弹出层 */
	.popup {
		position: fixed;
		left: 0;
		top: 0;
		right: 0;
		bottom: 0;
		z-index: 999;
		&.show {
			display: block;
			.mask{
				animation: showPopup 0.2s linear both;
			}
			.layer {
				animation: showLayer 0.2s linear both;
			}
		}
		&.hide {
			.mask{
				animation: hidePopup 0.2s linear both;
			}
			.layer {
				animation: hideLayer 0.2s linear both;
			}
		}
		&.none {
			display: none;
		}
		.mask{
			position: fixed;
			top: 0;
			width: 100%;
			height: 100%;
			z-index: 1;
			background-color: rgba(0, 0, 0, 0.4);
		}
		.layer {
			font-size: 30upx;
			position: fixed;
			z-index: 99;
			bottom: 0;
			width: 100%;
			min-height: 15vh;
			border-radius: 10upx 10upx 0 0;
			background-color: #fff;
		}
		.layer_goods{
			float: left;
			padding: 30upx;
			border-bottom: 0.5upx solid #C0C0C0;
			width: 100%;
			height: 150upx;
		}
		.layer_goods image{
			float: left;
			width: 140upx;
			height: 140upx;
			margin-right: 20upx;
		}
		.right_info{
			float: left;
			font-size: 30upx;
		}
		.layer_heng{
			width: 100%;
			height: 100upx;
			border-bottom: 0.5upx solid #C0C0C0;
			margin: 30upx 0upx;
			padding-bottom: 20upx;
			
		}
		.layer_text{
			width: 100%;
			margin-right: 100upx;
			padding-left: 40upx;
		}
		.layer_spec{
			margin-bottom: 20upx;
			border-radius: 10upx;
			background-color: #f5f5f5;
			padding:8upx;
			width:42%;
			height: 50upx;
			float: left;
			margin-left: 4%;
			border: #f5f5f5 0.5upx solid;
		}
		.layer_spec_class{
			color: #219975;
			margin-bottom: 20upx;
			border-radius: 10upx;
			border: #219975 0.5upx solid;
			background-color: #f6fffb;
			padding:8upx;
			width:42%;
			height: 50upx;
			float: left;
			margin-left: 4%;
		}
		.but{
			width: 700upx;margin: 0 auto; border-radius: 50upx;background-color: #1e936b;text-align: center;color: #FFFFFF;margin-bottom: 50upx;padding: 20upx 0;
			margin-left: 20upx;
		}
		@keyframes showPopup {
			0% {
				opacity: 0;
			}
			100% {
				opacity: 1;
			}
		}
		@keyframes hidePopup {
			0% {
				opacity: 1;
			}
			100% {
				opacity: 0;
			}
		}
		@keyframes showLayer {
			0% {
				transform: translateY(120%);
			}
			100% {
				transform: translateY(0%);
			}
		}
		@keyframes hideLayer {
			0% {
				transform: translateY(0);
			}
			100% {
				transform: translateY(120%);
			}
		}
	}
	.purchasing-dl {
		margin-top: 20upx;
		color: #FFFFFF;
		text-align: center;
		font-size: 28upx;
	}
	.purchasing-button1 {
		margin-top: 20upx;
		background: url(../../../static/buuton1.png);
		background-size:100% 100%;
		float:left ;
		width: 220upx;
		height: 80upx;
		margin-left: 60upx;
	}
	.purchasing-button2 {
		margin-top: 20upx;
		background: url(../../../static/buuton2.png);
		background-size:100% 100%;
		float:left ;
		width: 220upx;
		height: 80upx;
	}
	.purchasing-foot {
		border-top: 1upx solid #f3f3f3;
		width: 100%;
		height: 110upx;
		font-size: 20upx;
		background: #ffffff;
		position: fixed;
		width: 100%;
		z-index: 900;
		bottom: 0;
		left: 0;
		
		-moz-box-shadow: 0px -2px 5px #f1f1f1;
		-webkit-box-shadow: 0px -2px 5px #f1f1f1;
		box-shadow: 0px -2px 5px #f1f1f1;
		
		
	}
	.purchasing-path {
		width: 90upx;
		align-items: center;
		height: 100upx;
		float: left;
		font-size: 20upx;
		margin-left: 20upx;
		margin-top: 10upx;
	}
	.purchasing-path image {
			width: 65%;
			height: 56upx;
			margin-left: 20%;
			margin-top: 8upx;
		}
	page{
		overflow-x:hidden;
	}
	.title{
		font-size: 30upx;
		margin: 0 auto;
		width: 260upx;
		padding-top: 20upx;
	}
	.title image{
		width: 16upx;
		height: 24upx;
	}
	.select{
		font-size: 30upx;
		margin-bottom: 10upx;
		width: 100%;
		height: 50upx;
	}
	.select_text{
		float: left;
	}
	.select image{
		float: right;
		width: 20upx;
		height: 30upx;
		margin-top: 5upx;
	}
	.swiper-item image {
		width: 100%;
		height: 380upx;
	}
	.goods_class{
		margin-left: 48upx;
		width: 100%;
		height: 100upx;
	}
	.goods_class image{
		float: left;
		width: 90upx;
		height: 100upx;
		margin-left: 10upx;
	}
	.goods_class_text{
		float: left;
		font-size: 30upx;
		margin-top: 30upx;
		margin-left: 20upx;
		color: #afafaf;
		background-color: #f1f1f1;
	}
	.content {
		margin: 20upx;
	}
	.content_back{
		width: 100%;
		height: 80upx;
		background-color: #f5f5f5;
	}
	.pd-desc-detail {
		font-size: 30upx;
		margin: 15upx 0;
	}
	.pd-desc-price {
		float: left;
		font-size: 27upx;
		color: #999999;
	}
	.pd-desc-sale {
		font-size: 27upx;
		float: right;
		color: #b2b2b2;
	}
	.pd-desc-info{
		    margin-bottom: 20upx;
		    height: 40upx;
	}
</style>
