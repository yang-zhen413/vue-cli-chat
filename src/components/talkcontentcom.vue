<template>
	<div class="talk-list">
		<div class="talk-item" v-for="item,index in talkList" :key="index">
			<div class="talk-head">
				<img :src="item.user.headimg">
			</div>
			<div class="talk-content">
				<div class="bg">
					<div class="right_triangle"></div>
					<span>{{item.talkcontent}}</span>
				</div>
			</div>
		</div>
	</div>
</template>

<script>
	export default{
		props:['talkList']
	}
</script>

<style scoped>
	.talk-list{
		height: 310px;
		width: 480px;
		border-bottom:1px solid #ccc;
		/*border-right: 1px solid #ccc;*/
		/*background-color: rgb(245,245,245);*/
		padding: 10px;
		overflow:auto;
	}

	/*修改滚动条样式*/
	.talk-list::-webkit-scrollbar{
	  width:5px;
	  height:5px;
	  /**/
	}
	.talk-list::-webkit-scrollbar-track{
	  background: rgb(239, 239, 239);
	  border-radius:2px;
	}
	.talk-list::-webkit-scrollbar-thumb{
	  background: #bfbfbf;
	  border-radius:10px;
	}
	.talk-list::-webkit-scrollbar-thumb:hover{
	  background: #333;
	}
	.talk-list::-webkit-scrollbar-corner{
	  background: #179a16;
	}

	.talk-item{
		/*display: flex;*/
		overflow: hidden;
        position: relative;
        margin-bottom: 10px;
	}
	.talk-head {
        position: absolute;
        right: 0;
        cursor: pointer;
    }

    .talk-content {
        min-width: 100px;
        padding: 0 50px;
        line-height: 23px;
    }
    .talk-item .talk-content .bg {
        margin: 5px 20px 10px 15px;
        border-radius: 7px;
        padding: 10px;
        display: inline-block;
        position: relative;
        background-color: rgb(255,255,255);
        float: right;
    }
    .talk-item .talk-head img {
        width: 50px;
        height: 50px;
    }

    .left_triangle {
        height: 0px;
        width: 0px;
        border-width: 8px;
        border-style: solid;
        border-color: transparent rgb(255,255,255) transparent transparent;
        position: absolute;
        left: -15px;
        top: 15px;
    }
    .right_triangle {
        height: 0px;
        width: 0px;
        border-width: 8px;
        border-style: solid;
        border-color: transparent transparent transparent rgb(255,255,255);
        position: absolute;
        right: -15px;
        top: 15px;
    }
	/*.talk-head>img{
		width: 	45px;
		height: 45px;
	}
	.talk-content{
		max-width: 200px;
		background-color: rgb(255,255,255);
		padding: 3px 5px;
		border-radius: 5px;
		border: 1px solid rgb(231,231,231);
		margin-left: 5px;
		font-size: 14px;
	}*/
</style>