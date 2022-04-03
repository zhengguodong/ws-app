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
				if(this.formData.name!=''&&this.formData.password!=''){
					uni.request({
					method:"POST",
					url:"http://localhost:8082/login",
					data:{
						username:this.formData.name,
						password:this.formData.password
					},
					success:(res)=>{
						uni.setStorageSync("id",res.data.data.id)
						uni.setStorageSync("autograph",res.data.data.autograph)
						uni.setStorageSync("name",res.data.data.name||res.data.data.username)
						console.log("login",res)
						if(res.data.code==200){
							uni.showToast({
								icon:"success",
								title:"登录成功！"
							})
							setTimeout(()=>{
								uni.switchTab({
								url:"../home/home"
								})
							},500)
							
						}else{
							uni.showToast({
								icon:"error",
								title:"账号或密码错误，请重新输入！"
							})
						}
						
					},
					fail:()=>{
						uni.showToast({
							icon:"error",
							title:"请联系管理员！"
						})
					}
				})
				}else{
					uni.showToast({
						icon:"error",
						title:"请完整输入信息！"
					})
				}
				
				
			},
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
