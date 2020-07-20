<template>
	<view>
		<view class="title">
			<label>购物车</label>
		</view>
		<view class="text" @click="updatitle(title)">{{title}}</view>
		
		<view>
		   <view class="product">
				<view class="pitchon" v-for="(items,index) in data_goods" :key="index">
					<view class="pitchon_left">
						<image class="circle" :src="items.class ? '../../../static/class_ico.png' : '../../../static/class_ico1.png'" mode="" @click="tabgoods_list(index)"></image>
						<image class="drawing" :src="items.img" mode=""></image>
					</view>
					<view class="pitchon_right">
						<text class="GoodsTitle">商品名称</text>
						<!-- <view class="drug">规格：<text>20*24片</text></view> -->
						<!-- <view class="vender">生产厂家：<text>{{items.manufacturer}}</text></view> -->
						<view style="margin-top: 70upx;">
							<text class="discounts">￥20.00</text>
							<!-- <text class="original">￥{{items.goodsprice}}</text> -->
						</view>
						<view class="price">
							<text class="add" @click="sumupdate(index,'add')">+</text>
							<text class="goods_sum" type="text">{{items.sum}}</text>
							<text class="subtract" @click="sumupdate(index,'cut')">-</text>	
						</view>
					</view>
				</view>
			</view>
			<!-- 去结算 -->
			<view class="close">
				<view class="twenty" @click="allgoods(style)">
					<image class="multi" :src="style ? '../../../static/class_ico.png' : '../../../static/class_ico1.png'" mode=""></image>
					<text style="font-size: 35upx;">全选</text>
				</view>
				<!-- <view class="count">合计:<text>￥{{total}}</text></view> -->
				<view class="forty" v-if="title == '管理'">
					<button class="btnRed" @click="AddOrder"><label style="padding-bottom: 10upx;">结算(0)</label></button>
				</view>
				<view class="forty" v-else>
					<button class="btnRed1"><label style="padding-bottom: 10upx;">删除</label></button>
				</view>
				<view style="clear: both;"></view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				style:false,
				title:'管理',
				data_goods: [
					{img:'../../../static/goods_ico.png',title: '两用6件（6-14）',class: false,sum:1},
					{img:'../../../static/goods_ico.png',title: '两用6件（6-14）',class: false,sum:1},
					{img:'../../../static/goods_ico.png',title: '两用6件（6-14）',class: false,sum:1}
				],
			}
		},
		onLoad() {
		},
		methods: {
			updatitle(title){
				if(title == '管理'){
					this.title = '完成'
				}else{
					this.title = '管理'
				}
			},
			allgoods(style){
				this.style = !this.style;
				if(style){
					for (var k in this.data_goods) {
						this.data_goods[k].class = false;
					}
				}else{
					for (var k in this.data_goods) {
						this.data_goods[k].class = true;
					}
				}
				
			},
			//选择单个药品
			tabgoods_list(index){
				this.data_goods[index].class = !this.data_goods[index].class;
			},
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
			addcart:function(){
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
		}
	}
</script>

<style lang="scss">
	.GoodsTitle{
		font-size: 30upx;
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
			width: 20%;
			float: left;
			margin-left: 20upx;
			.multi{
				width: 40upx;
				height: 40upx;
			    vertical-align: middle;
				margin-right: 12upx;
			}
		}
		.count{
			width: 40%;
			float: left;
		}
		.forty{
			float: right;
			width: 34%;
			
			.btnRed{
				width: 210upx;
				height: 80upx;
				background: #eca941;
				color: #FFFFFF;
				margin-top: 16upx;
				border-radius: 35upx;
				font-size: 32upx;
			}
			.btnRed1{
				width: 210upx;
				height: 80upx;
				background: #eca941;
				color: #FFFFFF;
				margin-top: 16upx;
				border-radius: 35upx;
				font-size: 32upx;
			}
		}
	}
	.product{
		width: 95%;
		top: 20upx;
		left: 0;
		margin: auto;
	}	
	.pitchon{
		border-radius: 10upx;
		margin-bottom: 20upx;
		height: 200upx;
		width: 100%;
		background: #FFFFFF;
		padding-top: 30upx;
	}
	.pitchon_left{
		vertical-align: middle;
		width: 40%;
		float: left;
		.circle{
			float: left;
			width: 40upx;
			height: 40upx;
			margin-left: 10%;
			margin-top: 24%;
		}
		.drawing{
			float: left;
			width: 180upx;
			height: 170upx;
			margin-left: 20upx;
			vertical-align: middle;
		}
	}
	.pitchon_right{
			float: left;
			width: 52%;
			top: 90upx;
			right: 100upx;
			
			.vender{
				color: #808080;
				font-size: 24upx;
				margin-top: 3%;
				overflow: hidden;
				white-space: nowrap;
				text-overflow: ellipsis;
			}
			.discounts{
				color: red;
				font-size: 30upx;
			}
			.original{
				color: #808080;
				font-size: 26upx;
				margin-left: 20upx;
				text-decoration: line-through;
			}
	}
	.price{
		position: absolute;
		right: 47upx;
		text-align: center;
	    text {
			width: 40upx;
			height: 40upx;
			// border: 2upx solid #808080;
			display: inline-block;
		}
		.goods_sum {
			position: absolute;
			bottom: 0upx;
			right: 62upx;
			height: 52upx;
			background-color: #f5f5f5;
			// border-top: 2upx solid #808080;
			// border-bottom: 2upx solid #808080;
		}
		.add{
			position: absolute;
			bottom: 10upx;
			right: 0;	
		}
		.subtract{
			position: absolute;
			bottom: 10upx;
			right: 124upx;
		
		}
	}
	page{
		background-color: #f5f5f5;
	}
	.title{text-align: center;font-size: 35upx;width: 100%;height: 60upx;padding-top: 20upx;}
	.text{
		font-size: 30upx;
		color: #808080;
		position: absolute;
		right: 20upx;
		top:20upx;
	}
</style>
