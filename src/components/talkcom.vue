<template>
	<div class="talk">
		<div class="header">
			<h3>{{currentUser.username}}</h3>
		</div>
		<!-- 聊天列表 -->
		<talkcontent-com :talkList='talkList'></talkcontent-com>
		<!-- 聊天输入窗口 -->
		<talkinput-com :sendMsg='sendMsg'></talkinput-com>
	</div>
</template>

<script>

	import talkinputCom from './talkinputcom'
	import talkcontentCom from './talkcontentcom'

	export default {
		data(){
			return {
				talkcontent:"",
				talkList:[
					
				]
			}
		},
		props:['currentUser'],
		components:{
			talkinputCom,talkcontentCom
		},
		methods:{
			sendMsg:function(content){
				this.talkList.push({
						user:{
							username:"小红",
							headimg:require('../assets/img/head1.jpg'),
						},
						talkcontent:content
					})
			}
		}
	}
</script>

<style scoped>
	.talk{
		width: 500px;
		height: 500px;
		/*background-color: yellow;*/
		/*border:1px solid #ccc;*/
		background-color: rgb(245,245,245);
	}
	.header h3{
		margin-left: 15px;
	}
	.header{
		width: 500px;
		height: 40px;
		border-bottom:1px solid #ccc;
		/*border-right: 1px solid #ccc;*/
		/*background-color: #ffffff;*/
		line-height:37px;
		margin-top: -20px;
	}
</style>