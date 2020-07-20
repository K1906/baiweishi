<template>
	<view>
		<view class="back">
			<view class="search">
				<view class="search-bar">
					<image src="../../static/search.png" mode="">
						<input type="text" confirm-type="search" placeholder="搜索" style="margin-left: 60upx;font-size: 30upx;color: #999999;" @focus="content_on" @confirm="content_yse"></input>
					</image>
				</view>
			</view>
			<view class="text_but">
				取消
			</view>
		</view>
		
		<view class="recording" v-if="style == 1">
			<view style="width: 100%;height: 70upx;float: left;margin-top: 40upx;">
				<label style="float: left;font-size: 30upx;">历史搜索</label>
				<label style="float: right;color: #999999;font-size: 27upx;margin-top: 8upx;" @click="delete_myArray">清除记录</label>
				<image src="../../static/delete.png" style="width: 30upx;height: 30upx;margin-right: 10upx;float: right;margin-top: 8upx;"></image>
			</view>
			
			<view>
				<label class="recording_text"  v-for="(item,index) in myArray" :key="index">{{item}}</label>
			</view>
		</view>
		
		<view v-else>
			<view style="margin-left:80upx;float: left;width: 680upx;">
				<label class="goods_class" @click="textclass(1)">
					<label :style="{color: index == 1 ?'#1e936b' : '#333333'}">热门</label>
					<label>
						<image :src="index1 ? '../../static/triangle_up.png' : '../../static/down1.png'" class="top"></image>
						<image :src="index1 ? '../../static/triangle_down.png' : '../../static/triangle_up1.png'" class="button"></image></label>
				</label>
				
				<label class="goods_class" @click="textclass(2)">
					<label :style="{color: index == 2 ? '#1e936b' : '#333333'}">价格</label>
					<image :src="index2 ? '../../static/triangle_up.png' : '../../static/down1.png'" class="top"></image>
					<image :src="index2 ? '../../static/triangle_down.png' : '../../static/triangle_up1.png'" class="button"></image>
				</label>
				
				<view class="filter" @click="drawer">
					<label style="float: left;">筛选</label>
					<image src="../../static/filter.png"></image>
				</view>
			</view>
			
			<view style="border: #C0C0C0 solid 0.5upx;width: 100%;margin-top: 14upx;float: left;"></view>
			
			<view class="pitchon" v-for="(items,index) in data_goods" :key="index" @click="linhgoods">
				<view class="pitchon_left">
					<image class="drawing" :src="items.img" mode=""></image>
				</view>
				<view class="pitchon_right">
					<text class="GoodsTitle">商品名称</text>
					<view style="margin-top: 70upx;">
						<text class="discounts" style="float: left;">￥ 2000</text>
						<text style="float: right;color: #999999">8522人已付款</text>
					</view>
				</view>
			</view>
			<uni-drawer :visible="show" mode="right" @close="noshow" :width='width'>
			    <view style="padding:30rpx;float: left;">
			        <view class="uni-title" style="font-size:30upx">价格区间</view>
					
					<view class="qujian">
						
						<input placeholder="输入最低价" class="qujian_text" style="font-size: 30upx;color: #999999;">
						<image src="../../static/line.png"></image>
						<input placeholder="输入最高价" class="qujian_text" style="font-size: 30upx;color: #999999;">
						
					</view>
			    </view>
				
				<view style="padding:30upx 0 0 30upx;float: left;">
				    <view class="uni-title" style="font-size:30upx">品牌</view>
					
					<view class="qujian">
						<label v-for="(item,index) in data_goods_text" :key="index" @click="brand(index)">
							<label :class="item.class ? 'brand':'brand1'">{{item.title}}</label>
						</label>
					</view>
				</view>
				
				<view style="left: 30upx;bottom: 30upx; position: absolute;">
					<view class="reset" @click="noshow">重置</view>
					<view class="determine" @click="noshow">确定</view>
				</view>
			</uni-drawer>
		</view>
	</view>
</template>

<script>
	import uniDrawer from "@/components/uni-drawer/uni-drawer.vue"
	export default {
		components: {uniDrawer},
		data() {
			return {
				width:540,
				style:1,
				show:false,
				title:'管理',
				index:1,
				index1:true,
				index2:true,
				data_goods: [
					{img:'../../static/goods_ico.png',title: '两用6件（6-14）',class: false,sum:1},
					{img:'../../static/goods_ico.png',title: '两用6件（6-14）',class: false,sum:1},
					{img:'../../static/goods_ico.png',title: '两用6件（6-14）',class: false,sum:1}
				],
				data_goods_text: [
					{title: '百威师',class: true},
					{title: '科普',class: false},
					{title: '融城',class: false},
					{title: '科普',class: false},
					{title: '融城',class: false}
				],
				myArray:[]
			}
		},
		onLoad() {
			this.myArray.push('百威师');
		},
		methods: {
			linhgoods(){
				uni.navigateTo({
					url:'goods/goodsDetails'
				})
			},
			content_on(e){
				this.style = 1;
			},
			delete_myArray(){
				this.myArray = [];
			},
			content_yse(e){
				this.myArray.push(e.detail.value);
				this.style = 0;
			},
			drawer(){
				this.show = true;
			},
			noshow(){
				this.show = false;
			},
			textclass(index){
				if(this.index == index){
					if(index == 1){
						this.index1 = !this.index1
					}else{
						this.index2 = !this.index2
					}
				}
				this.index = index;
			},
			
			brand(index){
				for (var k in this.data_goods_text) {
					this.data_goods_text[k].class = false;
				}
				this.data_goods_text[index].class = true;
			},
		}
	}
</script>

<style>
	.reset{
		-webkit-align-items:center;
		width: 220upx;
		height: 64upx;
		text-align: center;
		background-color: #ededed;
		color: #333333;
		font-size: 30upx;
		margin-right: 30upx;
		float: left;
		padding-top: 20upx;
	}
	.determine{
		padding-top: 20upx;
		align-items:center;/*新版本*/
		float: left;
		width: 220upx;
		height: 64upx;
		text-align: center;
		background-color: #eca941;
		color: #FFFFFF;
		font-size: 30upx;
	}
	.brand{
		padding: 14upx 30upx;
		font-size: 30upx;
		background-color: #333333;
		color: #ffffff;
		margin-right: 30upx;
		float: left;
		margin-bottom: 30upx;
	}
	.brand1{
		margin-bottom: 30upx;
		float: left;
		padding: 14upx 30upx;
		font-size: 30upx;
		background-color: #ededed;
		color: #333333;
		margin-right: 30upx;
	}
	.qujian_text{
		font-size: 30upx;color: #d8d8d8;text-align: center;
	}
	.qujian image{
		width: 70upx;
		height:5upx;
		float:left;
		margin: 30upx 10upx 0 10upx;
	}
	.qujian{
		margin-top: 30upx;
	}
	.qujian input{
		width: 190upx;height: 70upx;float: left;background-color: #ededed;border-radius: 32upx;
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
		border-radius: 10upx;
		float: left;
		width: 180upx;
		height: 170upx;
		margin-left: 20upx;
		vertical-align: middle;
	}
	.pitchon{
		float: left;
		margin-bottom: 20upx;
		height: 200upx;
		width: 100%;
		background: #FFFFFF;
		padding-top: 30upx;
		border-bottom: #C0C0C0 0.5upx solid;
	}
	.pitchon_right{
			float: left;
			width: 65%;
			top: 90upx;
			right: 100upx;
			font-size: 30upx;
	}
	.button{
		position: relative;
		top: 6upx;
	}
	.top{
		 position: relative;
		 left: 16upx;
		 top: -16upx;
	}
	.filter{
		width: 120upx;
		font-size: 35upx;
		height: 60upx;
		padding-top: 20upx;
		float: left;
	}
	.filter image{
		width: 30upx;
		height: 34upx;
		padding-top: 8upx;
		float: left;
		margin-left: 10px;
	}
	.goods_class{
		width: 100upx;
		font-size: 35upx;
		height: 60upx;
		padding-top: 20upx;
		float: left;
		margin-right: 140upx;
	}
	.goods_class image{
		width: 16upx;
		height: 12upx;
	}
	.recording_text{
		padding: 10upx 30upx;
		margin-right: 30upx;
		color: #999999;
		background-color: #ededed;
		font-size: 30upx;
		border-radius: 25upx;
	}
	.recording{
		width: 700upx;
		margin: 0 auto;
		
	}
	.back{
		background-color: #f1f1f1;
		height: 120upx;
		width: 100%;
		float: left;
	}
	.search {
		float: left;
		color: #808080;
		height: 75upx;
		background-color: #FFFFFF;
		border-radius: 5px;
		width: 600upx;
		margin-top: 22upx;
		margin-bottom: 20upx;
		font-size: 30upx;
		margin-left: 30upx;
	}
	.search-bar {
		padding-top: 20upx;
	}
	.search-bar image{
		width: 30upx;height: 30upx;float: left;margin-left: 20upx;margin-right: 20upx;margin-top: 4upx;
	}
	.text_but{
		float: left;
		padding-top: 40upx;
		font-size: 30upx;
		padding-left: 30upx;
		color: #1e936b;
	}
</style>
