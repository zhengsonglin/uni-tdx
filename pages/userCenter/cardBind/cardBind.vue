<template>
	<view class="vh100">
		<cu-custom bgColor="bg-gradual-green" :isBack="true">
				<view slot="backText">返回</view>
				<view slot="content">绑定银行卡</view>
			</cu-custom>
			<form class="bg-white">
		        <view class="cu-form-group">
		            <view class="title">手机号码</view>
		            <input placeholder="请输入手机号码" maxlength="11"></input>
		            <view class="cu-capsule radius">
		                <view class="cu-tag bg-blue">+86</view>
		                <view class="cu-tag line-blue">中国大陆</view>
		            </view>
		        </view>
		        <view class="cu-form-group">
		            <view class="title">手机验证码</view>
		            <input placeholder="请输入短信验证码" maxlength="6"></input>
		            <button class="cu-btn bg-green shadow">获取验证码</button>
		        </view>
		        <view class="cu-form-group">
					<view class="title">真实姓名</view>
					<input placeholder="请输入真实姓名" class="text-right"></input>
				</view>
		        <view class="cu-form-group">
		            <view class="title">开户银行</view>
		            <picker @change="bankPickerChange" range-key="name" header-text="开户行" :value="bankIndex" :range="bankPickerOptions">
		                <view class="picker">
		                    {{bankIndex?bankPickerOptions[bankIndex]['name']:'请选择开户银行'}}
		                </view>
		            </picker>
		        </view>
		        <view class="cu-form-group">
		            <view class="title">开户地区</view>
		            <picker mode="region" @change="RegionChange" :value="region" :custom-item="customItem">
		                <view class="picker">
		                    {{region[0]}}，{{region[1]}}，{{region[2]}}
		                </view>
		            </picker>
		        </view>
		        <view class="cu-form-group">
					<view class="title">开户支行</view>
					<input placeholder="请输入开户支行" class="text-right"></input>
				</view>
		        <view class="cu-form-group">
					<view class="title">银行卡号</view>
					<input placeholder="请输入银行卡号" class="text-right" placeholder-class="text-df"></input>
				</view>
		        <view class="padding flex flex-direction">
		            <button class="cu-btn bg-gradual-green margin-tb-sm lg">提交</button>
		        </view>
		    </form>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				bankIndex: null,
				bankPickerOptions: [
					{name:"中国农业银行", id:"10806310"},
					{name:"中国工商银行", id:"10806311"},
					{name:"中国银行", id:"10806312"},
					{name:"交通银行", id:"10806313"},
					{name:"招商银行", id:"10806325"},
				],
				region: ['广东省', '广州市', '海珠区']
			};
		},
		methods:{
			bankPickerChange(e) {
				console.log(e);
				this.bankIndex = e.detail.value
			},
			RegionChange(e) {
				this.region = e.detail.value
			},
		}
	}
</script>

<style lang="scss" scoped>
	.cu-form-group .title{
	    width: 200rpx;
	}
</style>
