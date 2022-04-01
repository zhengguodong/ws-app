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
							<uni-data-checkbox  :multiple="false" v-model="formData.value" :localdata="formData.range" @change="change" ></uni-data-checkbox>
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
						value: '',
						range: [{"value": 0,"text": "男"},{"value": 1,"text": "女"}],
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
						// 对email字段进行必填验证
						email: {
							rules: [
							// 	{
							// 	format: 'email',
							// 	errorMessage: '请输入正确的邮箱地址',
							// },
							{
								required: true,
								errorMessage: '请输入账号',
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
				/**
				 * 复写 binddata 方法，如果只是为了校验，无复杂自定义操作，可忽略此方法
				 * @param {String} name 字段名称
				 * @param {String} value 表单域的值
				 */
				// binddata(name,value){
				// 通过 input 事件设置表单指定 name 的值
				//   this.$refs.form.setValue(name, value)
				// },
				// 触发提交表单
				submit() {
					this.$refs.form.validate().then(res=>{
						setTimeout(()=>{
							uni.navigateTo({
							url:"../login/login"
						})
						},1000)
						
						this.$refs.popup.open('center')
						console.log('表单数据信息：', res);
					}).catch(err =>{
						console.log('表单错误信息：', err);
					})
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
