<template>
	<view class="vh100 bg-white">
		<cu-custom bgColor="bg-gradual-green" :isBack="true">
			<view slot="backText">返回</view>
			<view slot="content">添加意见</view>
		</cu-custom>
		
		<form>
			<view class="cu-form-group align-start">
				<view class="title">标题</view>
				<textarea maxlength="-1"  bindinput="textareaBInput" placeholder="多行文本输入框"></textarea>
			</view>
			<view class="cu-form-group align-start">
				<view class="title">内容</view>
				<textarea maxlength="-1"  bindinput="textareaBInput" placeholder="多行文本输入框"></textarea>
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
				
			};
		}
	}
</script>

<style lang="scss">

</style>
