<template>
	<view class="vh100 bg-white">
		<cu-custom bgColor="bg-gradual-green" :isBack="true">
			<view slot="backText">返回</view>
			<view slot="content">熊抢购</view>
		</cu-custom>
		<view class="cu-bar search bg-white fixed" :style="{'top':CustomBar+'px'}">
			<view class="search-form round">
				<text class="cuIcon-search"></text>
				<input type="text" placeholder="搜索图片、文章、视频" confirm-type="search"></input>
			</view>
			<view class="action">
				<button class="cu-btn bg-green shadow-blur round">搜索</button>
			</view>
		</view>
		<scroll-view scroll-x="true" class="bg-white nav fixed" scroll-with-animation :scroll-left="scrollLeft" 
			:style="{'top': (CustomBar+50)+'px'}">
			<view :class="['cu-item', {'text-green cur':item.id==TabCur}]" v-for="(item,index) in categoryList" :key="item.id" @click="tabSelect(item, index)">
				{{item.short_name}}
			</view>
		</scroll-view>
	
		<scroll-view scroll-y="true" class="scroll-content" 
			:style="{'height': 'calc(100vh - ' + CustomBar + 'px - 50px - 45px)'}">
			<view class="bg-white padding-sm">
				<view class="grid col-2 margin-bottom text-center">
					<view class="padding shadow-warp" v-for="(item, index) in curProducts" :key="item.pa_id">
						<view><image :src="item.img" mode="aspectFit" :lazy-load="true" class="response product-img"></image></view>
						<view class="text-cut text-bold text-darkGray text-sm">{{item.title}}</view>
						<view class="flex margin-xs">
							<text class="text-red text-line-through">￥{{item.price}}</text>
							<view class="text-red border margin-left-sm flex text-sm align-center">
								<text class="bg-red text-white padding-lr-xs">返利</text><text class="padding-lr-xs">￥2.80</text>
							</view>
						</view>
						<view class="flex justify-between align-center">
							<view class="bg-red text-white text-sm padding-lr-sm lowerPrice">最低价<text>{{item.price }}</text></view>
							<image mode="widthFix" class="baseImg" :lazy-load="true" src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAB4AAAAeCAYAAAA7MK6iAAAAGXRFWHRTb2Z0d2FyZQBBZG9iZSBJbWFnZVJlYWR5ccllPAAAAyFpVFh0WE1MOmNvbS5hZG9iZS54bXAAAAAAADw/eHBhY2tldCBiZWdpbj0i77u/IiBpZD0iVzVNME1wQ2VoaUh6cmVTek5UY3prYzlkIj8+IDx4OnhtcG1ldGEgeG1sbnM6eD0iYWRvYmU6bnM6bWV0YS8iIHg6eG1wdGs9IkFkb2JlIFhNUCBDb3JlIDUuNi1jMTQyIDc5LjE2MDkyNCwgMjAxNy8wNy8xMy0wMTowNjozOSAgICAgICAgIj4gPHJkZjpSREYgeG1sbnM6cmRmPSJodHRwOi8vd3d3LnczLm9yZy8xOTk5LzAyLzIyLXJkZi1zeW50YXgtbnMjIj4gPHJkZjpEZXNjcmlwdGlvbiByZGY6YWJvdXQ9IiIgeG1sbnM6eG1wPSJodHRwOi8vbnMuYWRvYmUuY29tL3hhcC8xLjAvIiB4bWxuczp4bXBNTT0iaHR0cDovL25zLmFkb2JlLmNvbS94YXAvMS4wL21tLyIgeG1sbnM6c3RSZWY9Imh0dHA6Ly9ucy5hZG9iZS5jb20veGFwLzEuMC9zVHlwZS9SZXNvdXJjZVJlZiMiIHhtcDpDcmVhdG9yVG9vbD0iQWRvYmUgUGhvdG9zaG9wIENDIChXaW5kb3dzKSIgeG1wTU06SW5zdGFuY2VJRD0ieG1wLmlpZDpFQjJCMDI0RjBGRkExMUVBODczQUM4NTlDOTZCNTZBMSIgeG1wTU06RG9jdW1lbnRJRD0ieG1wLmRpZDpFQjJCMDI1MDBGRkExMUVBODczQUM4NTlDOTZCNTZBMSI+IDx4bXBNTTpEZXJpdmVkRnJvbSBzdFJlZjppbnN0YW5jZUlEPSJ4bXAuaWlkOkVCMkIwMjREMEZGQTExRUE4NzNBQzg1OUM5NkI1NkExIiBzdFJlZjpkb2N1bWVudElEPSJ4bXAuZGlkOkVCMkIwMjRFMEZGQTExRUE4NzNBQzg1OUM5NkI1NkExIi8+IDwvcmRmOkRlc2NyaXB0aW9uPiA8L3JkZjpSREY+IDwveDp4bXBtZXRhPiA8P3hwYWNrZXQgZW5kPSJyIj8+7hv6RQAAA6BJREFUeNrEl2lsTVsUx3/3ltLWVDOlMVV4xmgiiCAR8xBi/GAInob4IAgxRoiIMcJ7RaSJRIiIKURiKCHGxFRjDaXmUjXX2JZrLes251ZvOSS9XcnK3WfvdfZ/r+m/z/Ug4psUHi4/U0THicZRPHJXdKPock9iTo7HD7pPtBuhkSOivb1+T0MFqtJVdKrXH95Qy1hvMeb0VxLnpYSkaGCPB6o2gIhKzlzlWGg9oODcX0qp4KBynoTt0KIv5H2BTWPh4g7omADdp8O3r7BrBhz732yr1JND1ody1SBMtvzwEp5chdeP/xC4epyB/rAoA50nwrX90GGMP05hUKMxTE6G2DZQplzw3R9egB3TIP1MYd+kj32FZktHwPzrUCnGng8tE89zpPvmFrT7KnM3DsNNac0H5+DFPfM4rgsMXgFRVcQmF1Z2tkP8FlilfHXJ50B49wyepsLMsxAe6QCGCe9kyOHWdIf3Lwq/32kCDF1t40u7IWm4i+KKjYdBcuKzWyDtuOVbQbOzYMMQAc4zu2epNtZi+1kzbzv71WrmIsea05FJYvwP1GkFiX1g/2LoMRM2/ws9ZzuetxliGkw2BMxXqOGinXzf4NxWyP0MNZtYAWlxLJYiqtcWWvaTXKZb6N5nOe8lS4Q2j3c096OzFlHRBbAWgxaTAimg9nL/hbamuc64Jt4MhltHZfMvAXfPKbi811Hd54/7WCVLbrG14t2SJ1Ctkc31nge1m8Psi4XtJ+wuOtQq4VGQ88EFsIpWrvbs60f2fHwdXNnrrPeaA5HR/rX1ctg7EqGGVvW5nwruFRj6X1KmyjBpB28p61Wlyp6zoN0oAzv6H3zOdmxTdhqLKdnoel5AGrRefD6XwP0WWMXqSym7ILouxLQ0jawcnGbziyhe3osKsMl+7jLHysfaPioXtsGnNwV5N16K69V9ocooZy5BuLxseesKZb62I5y1txkuqlpB+y/yt5aEJ3mljVMPCdhDG+tlMHCpUWK+Xfppo0YlHK2JfLr9wdkpv/E4rLTcNPWd58t7hIFu2VgrcnkHyfFoqFjL5vQWykyTVjoJTboazeqNFV1HUrXQodcT611eEg3aw/BEI4KfyL1IWfLYIhEo7zJtj9SDLoHzi0Xz5VZiWgjTNTWvtZWe3pAb67x5HGz7IoFL7NMnBMBpJYB72+v/WxFqSVJgbdTkEIIeEF3l1T9QMtAvOyFi7hQTmBawfpLMUDIWzLzvAgwAR7gnISyU8Z4AAAAASUVORK5CYII=" alt=""/>
						</view>
						<view class="margin-top-sm">
							<view class="cu-btn sm margin-right-xs block custom-btn" @click="toDetal(item)">马上抢</view>
						</view>
					</view>
				</view>
			</view>
		</scroll-view>
	</view>
</template>

<script>
	import {mapState,mapMutations} from 'vuex'
	export default {
		data() {
			return {
				CustomBar: this.CustomBar,
				TabCur: 0,
				scrollLeft:0,
				categoryList:[
					{"id":0,"short_name":"全部","long_name":"全部商品",products:[]},
					//...app.globalData.category
				],
				curProducts:[]
			};
		},
		computed:{
			...mapState([
				'category'
			])
		},
		methods:{
			tabSelect(item, index) {
				uni.showLoading({
					title: '加载中...',
					mask: true
				});
		
				let curProducts = [];
				if(index){
					curProducts = [...this.categoryList[index].products]
				}else{
					this.categoryList.forEach((item)=>{
						curProducts.push(...item.products)
					})
				}
				
				setTimeout(()=>{
					this.TabCur = item.id,
					this.scrollLeft = (index-1)*60,
					this.curProducts = curProducts
					uni.hideLoading()
				},200)
			},
			toDetal(item){
				console.log(item)
				wx.navigateTo({
					url: '/pages/home/productDetail/productDetail?item='+JSON.stringify(item),
				})
			},
		},
		mounted() {
		 	this.categoryList.push(...this.category)
			let curProducts = [];
			this.categoryList.forEach((item)=>{
				 curProducts.push(...item.products)
			})
			this.curProducts = curProducts
			uni.hideLoading()
		},
		 /**
		  * 生命周期函数--监听页面加载
		  */
		onLoad: function (options) {
			uni.showLoading({
				title: '加载中...',
				mask: true
			});
		},
	}
</script>

<style lang="scss" scoped>
	.scroll-content{
		margin-top:95px
	}
	.scroll-content .border{
		border: 1px solid #e54d42;
	}
	.scroll-content .product-img{
		/* max-height: 148px; */
		height: 300rpx;
	}
	.scroll-content .lowerPrice{
		border-radius: 0 28rpx 28rpx 0;
	}
	.scroll-content .baseImg{
		width:38rpx;
		height:38rpx;
	}
	.scroll-content .custom-btn{
		color: #f50;
		border: 1px solid #f50;
		border-radius: 8rpx;
		box-shadow: 0 6rpx 6rpx 0 rgba(255,201,169,.43);
		font-size: 28rpx;
	}
</style>
