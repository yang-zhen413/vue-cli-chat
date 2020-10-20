<template>
  <!-- 提示弹窗 -->
  <div class="tips" v-show="tips.isshow">
    <h3>{{tips.title}}</h3>
  </div>
</template>

<script>
  export default{
    name: "tips",
    data () {
      return {
        tips:{
          isshow:false,
          title:""
        }
      }
    },
    created () {
      this.bus.$on("tips", (data)=>{
        this.tips = data
      })
    },
    // 检测tips变化，显示提示1.5s之后自动关闭，可根据实际情况自动修改时间
    watch:{
      tips:function(){
        if (this.tips.isshow) {
          setTimeout( ()=>{
            this.tips.isshow=false
          },1000)
        }
      }
    }
  }
</script>

<style scoped>
.tips{
  display: flex;
  justify-content: center;
  flex-direction: column;
  align-items: center;
  position: fixed;
  left: 0;
  top: 0;
  z-index: 999;
  width: 100%;
  height: 100%;
  color: #fff;
}
h3{
  padding: 5px 10px;
  font-size: 12px;
  line-height: 12px;
  background-color: rgba(0,0,0,0.8);
  border-radius: 4px;
  margin-right: -550px;
  margin-bottom: -340px;
}
</style>