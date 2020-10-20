<template>
	<div class="friend">
		<div class="header">
			<h3>好友列表</h3>
		</div>
		<div class="list">
			<ul>
				<li :class="{in:index==current}" v-for="item,index in userlist" :key="'userlist'+index" @click="chooseUser(index)">
					<img :src="item.headimg">
					<h4>{{item.username}}</h4>
				</li>
			</ul>
		</div>
	</div>
</template>

<script>

export default {
  data(){
    return {
    	current:-1
    }
  },
  props:['userlist'],
  methods:{
  	chooseUser:function(index){
  		// console.log(index)
  		this.$emit('chooseUser', index)
  		this.current = index
  		
  	}
  }
}
</script>	

<style type="text/css" media="screen" scoped>
	.friend{
		width:200px;
		height:500px;
		background:rgb(238,238,238);
		/*background:rgb(217,216,216);*/
	}
	.header{
		width: 200px;
		height: 40px;

		line-height:37px;
		margin-top: -20px;
	}
	.header h3{
		margin-left: 15px;
	}
	.list{
		width: 200px;
		height: 445px;
		overflow:hidden;
	}
	.list:hover{
		overflow: auto;
		overflow: scroll;
	}
	.list ul{
		overflow: hidden;
	}
	.list ul:hover{
		overflow: auto;
		overflow-x:hidden
	}
	.list ul li img{
		width:50px;
		height:50px;
	}
	.list ul li{
		width: 180px;
		padding: 2px 10px;
		list-style: none;
		display: flex;
		line-height: 10px;
		margin-left: -40px;
	}
	.list ul li h4{
		margin-left: 10px;
	}
	.in{
		background:rgb(217,216,216);
	}

	/*修改滚动条样式*/
	.list::-webkit-scrollbar{
	  width:2px;
	  height:0.1px;
	}
	.list::-webkit-scrollbar-track{
	  background: rgb(239, 239, 239);
	  border-radius:2px;
	}
	.list::-webkit-scrollbar-thumb{
	  background: #bfbfbf;
	  border-radius:10px;
	}
	.list::-webkit-scrollbar-thumb:hover{
	  background: #333;
	}
	/*.list::-webkit-scrollbar-corner{
	  background: #179a16;
	}*/
</style>