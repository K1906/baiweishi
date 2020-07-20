<template>
	<view class="wrap">
		<view class="title_text" v-if="id>0">
			编辑收货地址
		</view>
		<view class="title_text" v-else>
			添加收货地址
		</view>
		<view class="perInfo">
			<view class="per-form">
				<view style="width: 100%;background-color: #f2f2f2;height: 25upx;position: absolute;top: 464upx;" v-if="id>0"></view>
				<view class="content">
					<form @submit="formSubmit">
						
						<view class="row">
							<label>收货人：</label>
							<input type="text" name="contacts" placeholder="请填写联系人姓名" placeholder-class="placeClass" @input="nameChange" />
						</view>

						<view class="row">
							<label>手机号码：</label>
							<input type="text" name="phone" placeholder="请填写收货人手机号码" placeholder-class="placeClass" @input="telChange"/>
						</view>

						<view class="row" @click="showMulLinkageThreePicker">
							<label>选择地区：</label>
								<input type="text" :value="pickerText" name="ress" class="right" placeholder="请选择省/市/区" disabled="true" />
						</view>
						
						<view class="row">
							<label>详细地址：</label>
							<input type="text" name="address" placeholder="详细地址，例：A栋2308" placeholder-class="placeClass" @input="houseChange"/>
						</view>
						
						<view class="row" style="margin-top: 30upx;" v-if="id>0">
							<label style="width: 100%;">设置为默认地址</label>
							<switch checked color="#F0AD4E" @change="switch1Change" />
						</view>
						<view class="btn-area">
							<button formType="submit" :class="[btnTemp?'btn':'']">保存地址</button>
						</view>
					</form>
					<mpvue-city-picker :themeColor="themeColor" ref="mpvueCityPicker" :pickerValueDefault="cityPickerValueDefault"
					 @onCancel="onCancel" @onConfirm="onConfirm"></mpvue-city-picker>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	import mpvueCityPicker from '../../../components/mpvue-citypicker/mpvueCityPicker.vue'

	export default {
		components: {
			mpvueCityPicker
		},
		
		data() {
			return {
				id:0,
				index: 0,
				themeColor: '#007AFF',
				name: "",
				tel: "",
				user_id:"",
				pickerText: "",
				btnTemp: false,
				house:'',
				region: ['', '', ''],
				address_id:"",
				ediaddress:[],
				goods_type:'',
				cityPickerValueDefault: [0, 0, 1],
			};
		},
		
		onLoad: function (option) {
			this.id = option.id;
		},
		
		methods: {
			switch1Change: function (e) {
			     console.log('switch1 发生 change 事件，携带值为', e.target.value)
			},
					
			showMulLinkageThreePicker() {
				this.$refs.mpvueCityPicker.show()
			},
			onCancel(e) {
			},
			onConfirm(e) {
				var that = this;
				that.pickerText = e.label;
				that.checkInput();
			},
	
			nameChange(e) {
				var that = this;
				that.name = e.target.value;
				that.checkInput();
			
			},
			
			telChange(e) {
				var that = this;
				that.tel = e.target.value;
				that.checkInput();
			},
			
			
			
			houseChange(e) {
				var that = this;
				that.house = e.target.value;
				that.checkInput();
			},
			
			
			
			checkInput(){
				var that =this;
				if(that.name !=""&& that.tel !="" && that.house !="" && that.pickerText !=""){
					that.btnTemp =true;
				}else{
					that.btnTemp =false;
				}
				
			},
			
			formSubmit(e){
			
			}
		},
	}
</script>

<style lang="less">
	.title_text{
		font-size: 30upx;
		text-align: center;
		margin: 20upx 0; 
	}
    .wallet-top{
		margin:15upx 0;
	}
	.perInfo {
		border-top: 0upx solid #f2f2f2;
	}

	.row {
		display: flex;
		align-items: center;
		height: 100upx;
		border-bottom: 1px solid #f2f2f2;
		font-size: 28upx;
		line-height: 100upx;

		label {
			width: 160upx;
			display: inline-block;
		}

		input {
			width: 500upx;
			display: inline-block;
			// height: 100upx;
			// line-height: 100upx;
		}
	}

	button {
		background: #f2f2f2;
		font-size: 28upx;
		height: 90upx;
		line-height: 90upx;
		border-radius: 60upx;
		color:#666;
	}

	.placeClass {
		color: #b2b2b2;
	}

	.btn-area {
		margin-top: 100upx;
	}

	.btn {
		background: #219975;
		color: white;
	}
	.content{
		width: 90%;
		margin-left: 5%;
	}
	
</style>