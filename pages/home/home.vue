<template>
	<view>
		<view id="header">
			好友列表
			
		</view>
		<view id="bottom">
			<uni-list>
				<uni-list-item title="好友abc" clickable  @click="onClick" ></uni-list-item>
				<uni-list-item title="好友abc"  clickable @click="onClick($event,1)" ></uni-list-item>
				<uni-list-item title="好友abc"  clickable @click="onClick($event,1)" ></uni-list-item>
				<uni-list-item title="好友abc" clickable  @click="onClick" ></uni-list-item>
				<uni-list-item title="好友abc"  clickable @click="onClick($event,1)" ></uni-list-item>
				<uni-list-item title="好友abc"  clickable @click="onClick($event,1)" ></uni-list-item>
				<uni-list-item title="好友abc" clickable  @click="onClick" ></uni-list-item>
				<uni-list-item title="好友abc"  clickable @click="onClick($event,1)" ></uni-list-item>
				<uni-list-item title="好友abc"  clickable @click="onClick($event,1)" ></uni-list-item>
				<uni-list-item title="好友abc" clickable  @click="onClick" ></uni-list-item>
				<uni-list-item title="好友abc"  clickable @click="onClick($event,1)" ></uni-list-item>
				<uni-list-item title="好友abc"  clickable @click="onClick($event,1)" ></uni-list-item>
				<uni-list-item title="好友abc" clickable  @click="onClick" ></uni-list-item>
				<uni-list-item title="好友abc"  clickable @click="onClick($event,1)" ></uni-list-item>
				<uni-list-item title="好友abc"  clickable @click="onClick($event,1)" ></uni-list-item>
				<uni-list-item title="好友abc" clickable  @click="onClick" ></uni-list-item>
				<uni-list-item title="好友abc"  clickable @click="onClick($event,1)" ></uni-list-item>
				<uni-list-item title="好友abc"  clickable @click="onClick($event,1)" ></uni-list-item>
			</uni-list>
		</view>
		<view >
				<uni-fab
					horizontal="right"
					@fabClick="dian"
				></uni-fab>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {

			}
		},
		methods: {
			dian(){
				console.log("12111")
			},
			onClick(){
				uni.navigateTo({
					url:"../chat/chat"
				})
			}
		},
		onPullDownRefresh() {
			console.log("wwww")
			setTimeout(()=>{
				uni.stopPullDownRefresh()
			},2000)
		}
	}
</script>

<style lang="scss">
#header{
	width: 100%;
	height: 50px;
	line-height: 50px;
	text-align: center;
	font-size: 18px;
	border-bottom: solid 1px rgb(218, 220, 224);
	
}
</style>
