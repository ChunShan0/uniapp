<template>
	<view class="content">
		<view class="header">
			<text class="title">测试页面</text>
		</view>
		
		<view class="main-content">
			<view class="card">
				<text class="card-title">滚动内容演示</text>
				<scroll-view scroll-y class="scroll-vertical">
					<view class="scroll-item" v-for="(item, index) in 4" :key="index">
						<text class="item-text">滚动项 {{index + 1}}</text>
					</view>
				</scroll-view>
			</view>
			
			<view class="card">
				<text class="card-title">横向滚动演示</text>
				<scroll-view scroll-x="true" class="scroll-horizontal">
					<view class="scroll-box" v-for="(item, index) in 5" :key="index">
						<text class="box-text">Box {{index + 1}}</text>
					</view>
				</scroll-view>
			</view>
			
			<view class="info-cards">
				<view class="info-item">
					<text class="info-title">信息 1</text>
					<text class="info-content">详细内容区域 1</text>
				</view>
				<view class="info-item">
					<text class="info-title">信息 2</text>
					<text class="info-content">详细内容区域 2</text>
				</view>
				<view class="info-item">
					<text class="info-title">信息 3</text>
					<text class="info-content">详细内容区域 3</text>
				</view>
			</view>
		</view>
	</view>
</template>

<script setup>
// 系统导航栏会自动处理返回功能
</script>

<style lang="scss">
	.content {
		display: flex;
		flex-direction: column;
		min-height: 100vh;
		padding: 20rpx;
		background-color: #f5f5f5;
		
		.header {
			display: flex;
			align-items: center;
			justify-content: center;
			padding: 40rpx 0;
			
			.title {
				font-size: 36rpx;
				font-weight: bold;
				color: #333;
			}
		}
		
		.main-content {
			flex: 1;
			display: flex;
			flex-direction: column;
			gap: 30rpx;
			padding: 20rpx 0;
			
			.card {
				background-color: #ffffff;
				border-radius: 16rpx;
				padding: 30rpx;
				box-shadow: 0 2rpx 12rpx rgba(0, 0, 0, 0.1);
				
				.card-title {
					font-size: 32rpx;
					font-weight: 600;
					color: #333;
					margin-bottom: 20rpx;
					display: block;
				}
			}
			
			.scroll-vertical {
				height: 200rpx;
				background-color: #f8f8f8;
				border-radius: 8rpx;
				padding: 10rpx;
				
				.scroll-item {
					padding: 20rpx;
					margin-bottom: 10rpx;
					background-color: #ffffff;
					border-radius: 8rpx;
					
					.item-text {
						color: #666;
						font-size: 28rpx;
					}
				}
			}
			
			.scroll-horizontal {
				white-space: nowrap;
				background-color: #f8f8f8;
				border-radius: 8rpx;
				padding: 20rpx;
				
				.scroll-box {
					display: inline-block;
					width: 200rpx;
					height: 100rpx;
					margin-right: 20rpx;
					background-color: #ffffff;
					border-radius: 8rpx;
					
					display: inline-flex;
					align-items: center;
					justify-content: center;
					
					.box-text {
						color: #666;
						font-size: 28rpx;
					}
				}
			}
			
			.info-cards {
				display: flex;
				flex-direction: column;
				gap: 20rpx;
				
				.info-item {
					background-color: #ffffff;
					border-radius: 16rpx;
					padding: 20rpx;
					box-shadow: 0 2rpx 12rpx rgba(0, 0, 0, 0.1);
					
					.info-title {
						font-size: 30rpx;
						font-weight: 600;
						color: #333;
						margin-bottom: 10rpx;
						display: block;
					}
					
					.info-content {
						color: #666;
						font-size: 28rpx;
					}
					
					&:hover {
						transform: translateX(4rpx);
						transition: all 0.3s ease;
					}
				}
			}
		}
	}
</style>
