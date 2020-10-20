<template>
  <div id="app">
    <div class="content">
      <user-com @chooseUser="toggleuser" :userlist="userlist"></user-com>
      <talk-com :currentUser="currentUser" v-show="isCheck"></talk-com>
      <talknull-com v-show="!isCheck"></talknull-com>
      <tip-com></tip-com>
    </div>
  </div> 
</template>

<script>
import TalkCom from './components/talkcom.vue'
import UserCom from './components/usercom.vue'
import TipCom from './components/tipcom.vue'
import TalknullCom from './components/talknullcom.vue'

export default {
  name: 'App',
  components: {
    TalkCom,UserCom,TipCom,TalknullCom
  },
  data(){
    return {
      isCheck:false,
      userlist:[
        {
          username:'小红',
          headimg:require('./assets/img/head1.jpg')
        },
        {
          username:'小象',
          headimg:require('./assets/img/head2.jpg')
        },
        {
          username:'小象红',
          headimg:require('./assets/img/head3.jpg')
        },
        {
          username:'小红象',
          headimg:require('./assets/img/head1.jpg')
        }
      ],
      currentUser:{
          // username:'小红',
          // headimg:require('./assets/img/head1.jpg')
      }
    }
  },
  methods:{
    toggleuser:function(index){
      this.currentUser = this.userlist[index]
      this.isCheck = true
    }
  }
}
</script>

<style scoped>
  .content{
    display: flex;
    width: 700px;
    height: 500px;
    margin: 50px auto;
    border: 1px solid #ccc;
    border-radius: 5px;
  }
</style>
