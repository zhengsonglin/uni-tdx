<template>
	<view class="vh100 bg-white">
		<cu-custom bgColor="bg-gradual-green" :isBack="true">
			<view slot="backText">返回</view>
			<view slot="content">新手攻略</view>
		</cu-custom>
	
		<view class="cu-list menu sm-border">
			<view class="cu-item">
				<view class="content padding-tb-xs">
					<view class="text-black cell-title">1、注册账户</view>
					<view class="text-darkGray padding-left-sm cell-text">邀请码需介绍人提供，在介绍人的会员中心可以看到</view>
				</view>
			</view>
			<view class="cu-item arrow">
				<view class="content padding-tb-xs">
					<view class="text-black cell-title">2、实名认证</view>
					<view class="text-darkGray padding-left-sm cell-text">会员中心-“实名认证”模块里填写实名，需要提供：真实姓名、淘宝账号、对应支付宝截图</view>
				</view>
			</view>
			<view class="cu-item">
				<view class="content padding-tb-xs">				
					<text class="text-black cell-title">3、联系客服等待实名认证通过</text>
				</view>
			</view>
			<view class="cu-item arrow">
				<view class="content padding-tb-xs">
					<view class="text-black cell-title">4、绑定银行卡</view>
					<view class="text-darkGray padding-left-sm cell-text">会员中心-绑定银行卡模块填写对应信息</view>
				</view>
			</view>
			<view class="cu-item arrow">
				<view class="content padding-tb-xs">
					<view class="text-black cell-title">5、通过审核选取任务</view>
					<view class="text-darkGray padding-left-sm cell-text">进入首页领取任务，限量免单模块为免单任务；熊抢购模块为真实购买</view>
				</view>
			</view>
			<view class="cu-item">
				<view class="content padding-tb-xs">
					<view class="text-black cell-title">6、任务中心点击“开始任务”</view>
					<view class="text-darkGray padding-left-sm cell-text">查看任务流程及注意事项，将提供的关键词复制到淘宝首页搜索，找不到对应商品联系客服可更换关键词</view>
				</view>
			</view>
			<view class="cu-item">
				<view class="content padding-tb-xs">
					<view class="text-black cell-title">7、验证链接</view>
					<view class="text-darkGray padding-left-sm cell-text">找到对应宝贝后复制宝贝链接在平台验证</view>
				</view>
			</view>
			<view class="cu-item">
				<view class="content padding-tb-xs">
					<view class="text-black cell-title">8、淘宝付款</view>
					<view class="text-darkGray padding-left-sm cell-text">验证成功后浏览宝贝，拍下与平台价格一致的商品，价格不一致可按照任务金额提交后在平台申请售后</view>
				</view>
			</view>
			<view class="cu-item">
				<view class="content padding-tb-xs">
					<view class="text-black cell-title">9、提交订单号</view>
					<view class="text-darkGray padding-left-sm cell-text">将淘宝的订单编号复制，粘贴到平台验证链接的下方，填写金额，点击提交</view>
				</view>
			</view>
			<view class="cu-item">
				<view class="content padding-tb-xs">
					<view class="text-black cell-title">10、收货好评</view>
					<view class="text-darkGray padding-left-sm cell-text">收到礼品后，在淘宝收货好评</view>
				</view>
			</view>
			<view class="cu-item">
				<view class="content padding-tb-xs">
					<view class="text-black cell-title">11、上传好评截图</view>
					<view class="text-darkGray padding-left-sm cell-text">在任务中心-“已提交”-点击“上传好评截图”</view>
				</view>
			</view>
			<view class="cu-item">
				<view class="content padding-tb-xs">
					<view class="text-black cell-title">12、等待商家审核</view>
					<view class="text-darkGray padding-left-sm cell-text">审核时间最长为36小时</view>
				</view>
			</view>
			<view class="cu-item">
				<view class="content padding-tb-xs">
					<view class="text-black cell-title">13、返本金及提现</view>
					<view class="text-darkGray padding-left-sm cell-text">审核完成，返还本金到余额，点击申请提现</view>
				</view>
			</view>
			<view class="cu-item">
				<view class="content padding-tb-xs">
					<view class="text-black cell-title">14、对本操作有任何疑问均可联系淘大熊客服哦</view>
				</view>
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
	.cu-list .content .cell-title {
	    font-size: 28rpx;
	}
	.cu-list .content .cell-text {
	    font-size: 24rpx;
	}
</style>
