<template>
	<view id="mine">
		<view id="header">
			<img src="../../static/1a.jpg" alt="" style="width:100%;height: 100%;">
		</view>
		<view id="mid">{{name}}</view>
		<view id="dh">{{msg}} </view>
		<view id="bottom">
			<uni-list>
				<uni-list-item title="个人信息" clickable  @click="onClick" ></uni-list-item>
				<uni-list-item title="上传头像"  clickable @click="uptx" ></uni-list-item>
				<uni-list-item title="退出"  clickable @click="out" ></uni-list-item>
			</uni-list>
		</view>
	</view>
</template>

<script>
	import "../../style/donghua.css"
	export default {
		data() {
			return {
				msg:'',
				name:''
			}
		},
		onLoad() {
			this.msg=uni.getStorageSync("autograph")
			this.name=uni.getStorageSync("name")
		},
		methods: {
			onClick(){
				uni.navigateTo({
					url:"../information/information"
				})
			},
			uptx(){
				// uni.navigateTo({
				// 	url:"../tx/tx"
				// })
			},
			out(){
				uni.showToast({
					icon:"loading",
					title:"正在登出。。。。"
				})
				setTimeout(()=>{
					uni.redirectTo({
						url:"../login/login"
					})
				},1000)
				
			}
			
			
		},
		onPullDownRefresh() {
				console.log('refresh');
				setTimeout( ()=>{
					uni.stopPullDownRefresh();
				}, 1000);
			}
	}
</script>

<style lang="scss">
	#mine{
		width: 100%;
		height: 100%;
		display: flex;
		justify-content: center;
		align-items: center;
		flex-direction:column;
		
		#header{
			margin-top: 30px;
			width: 150px;
			height: 150px;
			background-color: pink;
			border-radius: 50%;
			overflow: hidden;
		}
		#mid{
			margin-top: 5px;
			width: 100%;
			height: 50px;
			line-height: 50px;
			text-align: center;
			font-size: 20px;
			// background-color: pink;
		}
		#bottom{
			width: 100%;
			position: absolute;
			bottom: 0px;
		}
		#dh{
			color: rgb(170, 85, 0);
			margin-top: 60px;
			animation: face 5s infinite ease-in-out;
		}
	}

</style>
