<template>
	<view>
		<uni-forms :modelValue="formData" style="margin-top: 10px;">
					<uni-forms-item required label="姓名" name="name">
						<uni-easyinput type="text" v-model="formData.name" />
					</uni-forms-item>
					<uni-forms-item required name="email" label="邮箱">
						<uni-easyinput multiple v-model="formData.email" />
					</uni-forms-item>
					<uni-forms-item required name="signature" label="个性签名">
						<uni-easyinput multiple v-model="formData.signature" />
					</uni-forms-item>
					<uni-forms-item required name="birthday" label="生日">
						<!-- <uni-easyinput multiple v-model="formData.birthday" /> -->
						<uni-datetime-picker type="date" :clear-icon="false" v-model="formData.birthday"/>
					</uni-forms-item>
				</uni-forms>
				<button @click="submitForm">修改</button>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				formData:{
					name:'',
					email:'',
					signature:'',
					birthday:''
					
				}
			}
		},
		mounted(){
			this.getdata();
		},
		methods: {
			submitForm(){
				if(this.formData.name!=''&&this.formData.email!=''&&this.formData.signature!=''&&this.formData.birthday!=''){
					uni.request({
					method:"POST",
					url:"http://localhost:8082/setInfo",
					data:{
						id:uni.getStorageSync("id"),
						name:this.formData.name,
						email:this.formData.email,
						autograph:this.formData.signature,
						birthday:this.formData.birthday
					},
					success: () => {
						uni.showToast({
							icon:"success",
							title:"修改成功！"
						})
						setTimeout(()=>{
							uni.switchTab({
							url:"../mine/mine"
							})
						},1000)
						
					}
				})
				}else{
					uni.showToast({
						icon:"error",
						title:"请完整填写数据！"
					})
				}
				
			},
			getdata(){
				uni.request({
					method:"POST",
					data:{
						id:uni.getStorageSync("id")
					},
					url:"http://localhost:8082/getdata",
					success: (res) => {
						this.formData.name=res.data.name;
						this.formData.email=res.data.email;
						this.formData.signature=res.data.autograph;
						this.formData.birthday=res.data.birthday.substring(0,10)
					}
				})
			}
		}
	}
</script>

<style>

</style>
