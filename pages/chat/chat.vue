<template>
	<view style="width: 100%;height: 100%;">
		<view id="main">
			
		</view>
		<view id="bottom">
			<uni-easyinput type="textarea" v-model="value" placeholder="请输入内容"></uni-easyinput>
			<button type="primary">发送</button>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				value:''
			}
		},
		methods: {
			
		}
	}
</script>

<style>
#main{
	width: 100%;
	
	background-color: #aaffff;
}
#bottom{
	width: 100%;
	border-top: 1px #3B4144 solid;
	position: absolute;
	bottom: 0px;
}
</style>
