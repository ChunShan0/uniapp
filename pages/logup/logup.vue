<template>
	<view class="content">
		<view class="header">
			<text class="title">用户注册</text>
		</view>
		
		<view class="main-content">
			<view class="register-section">
				<view class="form-item">
					<text class="label">用户名</text>
					<input 
						type="text" 
						v-model="formData.username" 
						placeholder="请输入用户名"
						class="input"
					/>
				</view>
				
				<view class="form-item">
					<text class="label">密码</text>
					<input 
						type="password" 
						v-model="formData.password" 
						placeholder="请输入密码"
						class="input"
					/>
				</view>
				
				<view class="form-item">
					<text class="label">确认密码</text>
					<input 
						type="password" 
						v-model="formData.confirmPassword" 
						placeholder="请再次输入密码"
						class="input"
					/>
				</view>
				
				<view class="buttons">
					<button 
						class="btn register-btn" 
						@click="handleRegister"
					>注册</button>
					<button 
						class="btn back-btn" 
						@click="goBack"
					>返回登录</button>
				</view>
			</view>
		</view>
	</view>
</template>

<script setup>
import { ref } from 'vue'

const formData = ref({
	username: '',
	password: '',
	confirmPassword: ''
})

const handleRegister = () => {
	// 表单验证
	if (!formData.value.username || !formData.value.password || !formData.value.confirmPassword) {
		uni.showToast({
			title: '请填写完整信息',
			icon: 'none'
		})
		return
	}
	
	// 密码一致性验证
	if (formData.value.password !== formData.value.confirmPassword) {
		uni.showToast({
			title: '两次输入的密码不一致',
			icon: 'none'
		})
		return
	}
	
	// 密码强度验证（至少6位）
	if (formData.value.password.length < 6) {
		uni.showToast({
			title: '密码长度至少6位',
			icon: 'none'
		})
		return
	}
	
	// 这里添加注册逻辑
	uni.showLoading({
		title: '注册中...'
	})
	
	// 模拟注册请求
	setTimeout(() => {
		uni.hideLoading()
		uni.showToast({
			title: '注册成功',
			icon: 'success',
			success: () => {
				// 注册成功后延迟返回登录页
				setTimeout(() => {
					uni.navigateBack()
				}, 1500)
			}
		})
	}, 1500)
}

const goBack = () => {
	uni.navigateBack()
}
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
			flex-direction: column;
			align-items: center;
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
			padding: 20rpx 0;
			
			.register-section {
				background-color: #ffffff;
				border-radius: 16rpx;
				padding: 40rpx 30rpx;
				margin: 20rpx;
				box-shadow: 0 2rpx 12rpx rgba(0, 0, 0, 0.1);
				
				.form-item {
					margin-bottom: 30rpx;
					
					.label {
						display: block;
						font-size: 28rpx;
						color: #333;
						margin-bottom: 10rpx;
					}
					
					.input {
						width: 100%;
						height: 80rpx;
						border: 2rpx solid #e5e5e5;
						border-radius: 8rpx;
						padding: 0 20rpx;
						font-size: 28rpx;
						
						&:focus {
							border-color: #007AFF;
						}
					}
				}
				
				.buttons {
					display: flex;
					gap: 20rpx;
					margin-top: 40rpx;
					
					.btn {
						flex: 1;
						height: 80rpx;
						line-height: 80rpx;
						border-radius: 40rpx;
						font-size: 28rpx;
						border: none;
					}
					
					.register-btn {
						background: linear-gradient(45deg, #007AFF, #0056b3);
						color: #ffffff;
						
						&:active {
							opacity: 0.8;
						}
					}
					
					.back-btn {
						background: #ffffff;
						border: 2rpx solid #007AFF;
						color: #007AFF;
						
						&:active {
							background: #f5f5f5;
						}
					}
				}
			}
		}
	}
</style> 