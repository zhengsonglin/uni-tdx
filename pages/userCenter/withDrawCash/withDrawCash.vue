<template>
	<view class="vh100 bg-white">
		<cu-custom bgColor="bg-gradual-green" :isBack="true">
			<view slot="backText">返回</view>
			<view slot="content">账户提现</view>
		</cu-custom>
		<form>
			<view class="cu-form-group">
				<view class="title">可提现金额:</view>
				<view>
					<text class="text-right text-green text-lg margin-right-sm">￥29.90</text>
					<text class="cuIcon-check text-green text-bold" style="font-size:40rpx"></text>
				</view>
			</view>
			<view class="cu-form-group">
				<view class="title">提现方式:</view>
				<view>
				<radio checked class="margin-right-sm"></radio><text>银行卡</text>
				</view>
			</view>
			<view class="cu-form-group">
				<view class="title">姓名:</view>
				<view>zheng.sl</view>
			</view>
			<view class="cu-form-group">
				<view class="title">银行名称:</view>
				<view>招商银行</view>
			</view>
			<view class="cu-form-group">
				<view class="title">银行卡号:</view>
				<view>621661300003720872</view>
			</view>
			<view class="cu-form-group">
				<view class="title">提现金额:</view>
				<view>520.36</view>
			</view>
			<view class="padding-lr padding-top flex flex-direction">
				<button class="cu-btn bg-gradual-green margin-tb-sm lg">提交申请</button>
			</view>
		</form>
	
		<!-- 用户相关说明 -->
		<view class="bg-orange margin radius light about-user padding-sm">
			<view>用户提现相关说明</view>
			<view class="margin-xs text-sm">
				<view>1、平台暂时只支持提现到银行卡账户</view>
				<view >2、在国家法定假日和双休日期间，用户可以申请提现，但会在假期后第一个工作日予以处理。由此造成的不便，请多多谅解！</view>
				<view>3、提现后需要2-3个工作日安排提现打款</view>
				<view>4、提现金额不得低于1元，提现的所有手续费均由平台承担</view>
				<view>5、如有相关问题，请联系平台客服咨询！</view>
			</view>
		</view>
	
		<view :class="['cu-modal', {'show':showModal}]">
			<view class="cu-dialog">
				<view class="cu-bar bg-red justify-end">
				<view class="content bg-red text-white">提醒</view>
				<view class="action" @click="hideModal">
					<text class="cuIcon-close text-white"></text>
				</view>
				</view>
				<view class="padding-sm margin-tb-sm" style="line-height:50rpx;font-size:26rpx;">
					<text>因财务调整，建议优先选择绑定招商银行卡，招行卡提现会更便捷快速，其他银行卡提现、到账时间不变</text>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				showModal: false
			};
		},
		methods:{
			hideModal(){
				this.showModal = false
			},
		},
		mounted(){
			setTimeout(()=>{
				this.showModal = true
			},200)
		},
	}
</script>

<style lang="scss" scoped>
	.about-user{
	    line-height: 40rpx;
	}
</style>
