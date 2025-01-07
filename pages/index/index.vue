<template>
	<view class="content">
		<view class="header">
			<image class="logo" src="/static/logo.png" mode="aspectFit"></image>
			<text class="title">欢迎使用 uni-app</text>
		</view>
		
		<view class="main-content">
			<view class="login-section">
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
				
				<view class="buttons">
					<button 
						class="btn login-btn" 
						@click="handleLogin"
					>登录</button>
					<button 
						class="btn register-btn" 
						@click="handleRegister"
					>注册</button>
				</view>
				
				<view class="options">
					<text class="forget-pwd" @click="handleForgetPwd">忘记密码？</text>
				</view>
			</view>
		</view>
	</view>
</template>

<script setup>
import { ref } from 'vue'

const formData = ref({
	username: '',
	password: ''
})

const handleLogin = () => {
	if (!formData.value.username || !formData.value.password) {
		uni.showToast({
			title: '请填写完整信息',
			icon: 'none'
		})
		return
	}
	
	// 这里添加登录逻辑
	uni.showLoading({
		title: '登录中...'
	})
	
	// 模拟登录请求
	setTimeout(() => {
		uni.hideLoading()
		uni.showToast({
			title: '登录成功',
			icon: 'success',
			success: () => {
				// 登录成功后延迟跳转，让用户看到成功提示
				setTimeout(() => {
					uni.navigateTo({
						url: '/pages/test1/test1',
						success: (res) => {
							console.log('跳转成功')
						},
						fail: (err) => {
							console.error('跳转失败:', err)
						}
					})
				}, 1500)
			}
		})
	}, 1500)
}

const handleRegister = () => {
	uni.navigateTo({
		url: '/pages/logup/logup'
	})
}

const handleForgetPwd = () => {
	uni.showToast({
		title: '请联系管理员重置密码',
		icon: 'none'
	})
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
			
			.logo {
				height: 200rpx;
				width: 200rpx;
				margin-bottom: 30rpx;
			}
			
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
			
			.login-section {
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
					
					.login-btn {
						background: linear-gradient(45deg, #007AFF, #0056b3);
						color: #ffffff;
						
						&:active {
							opacity: 0.8;
						}
					}
					
					.register-btn {
						background: #ffffff;
						border: 2rpx solid #007AFF;
						color: #007AFF;
						
						&:active {
							background: #f5f5f5;
						}
					}
				}
				
				.options {
					text-align: center;
					margin-top: 30rpx;
					
					.forget-pwd {
						font-size: 26rpx;
						color: #666;
						text-decoration: underline;
					}
				}
			}
		}
	}
</style>
