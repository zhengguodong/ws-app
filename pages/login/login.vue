<template>
	<view>
		
						<view style="display: flex;margin-top: 10px;line-height: 36px;white-space: nowrap;">
							账号：<uni-easyinput type="text" v-model="formData.name" placeholder="请输入账号" style="width: 100%;"/>
							</view>
					
						<view style="display: flex;margin-top: 10px;line-height: 36px;white-space: nowrap; margin-bottom: 10px;">
							密码：<uni-easyinput type="password" v-model="formData.password" placeholder="请输入密码" style="width: 100%;"/>
							</view>
			
						<button @click="login" type="primary">登入</button>
						<view style="margin-top: 10px;float: right;">
							<uni-icons type="staff-filled" size="30" @click="test"></uni-icons>
							注册
						</view>
						
				
	</view>
</template>

<script>
	export default {
		data() {
			return {
				formData:{
					name:"",
					password:""
				}
			}
		},
		methods: {
			login(){
				uni.switchTab ({
					url:"../home/home"
				})
			},
			register(){},
			test(){
				uni.navigateTo({
					url:"../register/register"
				})
			}
		}
	}
</script>

<style>
uni-easyinput{
	display: inline-block;
	width:50%;
}
</style>
