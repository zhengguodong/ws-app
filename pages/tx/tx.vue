<template>
	<view>
		<view>
			<h2>选择头像：</h2>
		</view>
		<view id="pic">
			<uni-file-picker 
			v-model="imageValue" 
			fileMediatype="image" 
			mode="grid" 
			@select="select" 
			@progress="progress" 
			@success="success" 
			@fail="fail" 
		/>
		</view>
		
				</view>
</template>

<script>
	export default {
		data() {
			return {
				imageValue:{}	,
				}
		},
		methods: {
			
		}
	}
</script>

<style>
/* #pic{
	display: flex;
	justify-content: center;
	align-items: center;
} */
</style>
