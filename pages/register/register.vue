<template>
	<view>
		<view style="margin-top: 10px;">
			<uni-forms ref="form" :modelValue="formData" :rules="rules" >
				<view>	
					<uni-forms-item label="账号" name="username" >
						<uni-easyinput type="text" v-model="formData.username" placeholder="请输入账号" />
					</uni-forms-item>
				</view>
					
					<uni-forms-item label="密码" name="password" >
						<uni-easyinput type="password" v-model="formData.password" placeholder="请输入密码" />
					</uni-forms-item>
					<uni-forms-item label="性别" name="value">
							<uni-data-checkbox  v-model="formData.value" :localdata="formData.range" @change="change" ></uni-data-checkbox>
					</uni-forms-item>
					<uni-forms-item label="邮箱" name="email">
						<uni-easyinput class="input" v-model="formData.email" type="text" placeholder="请输入邮箱" />
					</uni-forms-item>
				</uni-forms>
				<button @click="submit" type="primary">注册</button>
				<uni-popup ref="popup" type="message">
					<uni-popup-message type="success" message="成功消息" :duration="2000"></uni-popup-message>
				</uni-popup>
		</view>
			
	</view>
</template>

<script>
	export default {
		data() {
				return {
					
					// 表单数据
					formData: {
						username: '',
						password: '',
						email:'',
						value: 0,
						range: [{"value": 1,"text": "男"},{"value": 2,"text": "女"}],
					},
					rules: {
						// 对name字段进行必填验证
						username: {
							rules: [{
									required: true,
									errorMessage: '请输入账号',
								},
								{
									minLength: 3,
									maxLength: 10,
									errorMessage: '账号长度在 {minLength} 到 {maxLength} 个字符',
								}
							]
						},
				
						email: {
							rules: [
						
							{
								required: true,
								errorMessage: '请输入邮箱',
							}]
						},
						password: {
							rules: [{
									required: true,
									errorMessage: '请输入密码',
								}
							]
						},
						value: {
							rules: [{
									required: true,
									errorMessage: '请选择性别',
								}
							]
						},
						
					}
				}
			},
			methods: {
				submit() {
					if(this.formData.username!=''&&this.formData.password!=''&&this.formData.email!=''&&this.formData.value!=''){
						uni.request({
						method:"POST",
						url:"http://localhost:8082/register",
						data:{
							username:this.formData.username,
							password:this.formData.password,
							email:this.formData.email,
							gender:this.formData.value
							
						},
						success:(res)=>{
							if(res.data.code==200){
								uni.showToast({
									icon:"success",
									title:"注册成功！"
								})
								setTimeout(()=>{
									uni.navigateTo ({
									url:"../login/login"
									})
								},500)
								
							}else if(res.data.code==300){
								uni.showToast({
									icon:"error",
									title:"账号已被注册，请重新注册！"
								})
							}else{
								uni.showToast({
									icon:"error",
									title:"注册失败！"
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
				change(e){
					console.log(this.formData.value)
							console.log('e:',e);
							
						}
			}
	}
</script>

<style>

</style>
