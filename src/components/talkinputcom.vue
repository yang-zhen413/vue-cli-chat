<template>
	<div class="send-window">
		<div class="d-text">
			<textarea ref="textinput" v-model="inputvalue" @keydown.enter="send"></textarea>
		</div>
		<div class="d-button"><button @click="send">发送</button></div>
	</div>
</template>

<script>
	export default{
		props:['sendMsg'],
		data(){
			return {
				inputvalue:""
			}
		},
		methods:{
			send:function(e){
				// 阻止回车键换行
				if (e.preventDefault) e.preventDefault();
        		else window.event.value = false;

				if (this.inputvalue.length <=0) {
					// console.log(this.$emit)
					this.bus.$emit('tips',{ isshow:true,title:"不能发送空白信息" })
					this.$refs.textinput.focus();
					return false
				}

				this.sendMsg(this.inputvalue)
				this.inputvalue = ""
				this.$refs.textinput.focus();
			}
		}
	}
</script>

<style scoped>
	.send-window{
		height: 130px;
		width: 500px;
	}
	.d-text{
		width: 500px;
		height: 90px;
	}
	.d-button{
		width: 500px;
		height: 39px;
		background-color: rgb(255,255,255);
		/*border-bottom: 1px solid #ccc;*/
		/*background-color: white;*/
/*		line-height: 30px;*/
	}
	.d-text textarea{
		width: 480px;
		height: 90px;
		resize: none;
		border: none;
		outline: none;
		background-color: rgb(255,255,255);
		font-size: 24px;
	    padding: 5px 10px;

	    text-shadow: 0px 0px 0px #000;
	    -webkit-text-fill-color: transparent;
	}
	.d-text textarea::-webkit-input-placeholder{
	    text-shadow: none;
	    -webkit-text-fill-color: initial;
	}

	
	/*修改滚动条样式*/
	.d-text textarea::-webkit-scrollbar{
	  width:5px;
	  height:5px;
	  /**/
	}
	.d-text textarea::-webkit-scrollbar-track{
	  background: rgb(239, 239, 239);
	  border-radius:2px;
	}
	.d-text textarea::-webkit-scrollbar-thumb{
	  background: #bfbfbf;
	  border-radius:10px;
	}
	.d-text textarea::-webkit-scrollbar-thumb:hover{
	  background: #333;
	}
	.d-text textarea::-webkit-scrollbar-corner{
	  background: #179a16;
	}



	.d-button button{
		border-radius: 5px;
		float: right;
		margin-top: 12px;
		margin-right: 15px;
	}
	.d-button button:hover{
		background-color: rgb(18,150,17)
	}
</style>