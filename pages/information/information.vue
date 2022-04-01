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
						<uni-easyinput multiple v-model="formData.birthday" />
					</uni-forms-item>
				</uni-forms>
				<button @click="submitForm">Submit</button>
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
		methods: {
			
		}
	}
</script>

<style>

</style>
