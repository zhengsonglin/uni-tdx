<template>
	<view class="vh100">
		<cu-custom bgColor="bg-gradual-green" :isBack="true">
			<view slot="backText">返回</view>
			<view slot="content">推荐好友</view>
		</cu-custom>
		<view class="padding-sm">
			<view class="title text-bold text-lg">1、复制链接分享给好友或朋友圈</view>
			<view class="margin">http://www.taodaxiong.cn/Mobile/MobileRegister?code=30234671</view>
			<view class="title text-bold text-lg">2、长按二维码保存到手机分享给好友或朋友圈</view>
			<view class="rec_fri_img text-center padding-top-xl">
				<image src="/static/img/recommend-qrcode1.png" mode="aspectFit" class="qrcode"/>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			};
		}
	}
</script>

<style lang="scss" scoped>
	.scrollPage .rec_fri_img .qrcode{
	    width: 320rpx;
	    height: 320rpx;
	}
</style>
