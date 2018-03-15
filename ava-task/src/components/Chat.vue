<template>
  <div class="Chat" >
    <chat-side-menu :type="typeArray" :allUsers="allUsers"></chat-side-menu>
    <chat-side-menu-mobile :type="typeArray" :allUsers="allUsers"></chat-side-menu-mobile>
    <chat-block  :array="activeArray" :type="typeArray" :companionImg="companion"></chat-block>
  </div>
</template>

<script>
import Vue from 'vue'
import chatSideMenu from './chatItems/chatSideMenu'
import chatSideMenuMobile from './chatItems/mobile/chatSideMenuMobile'
import chatBlockMessage from './chatItems/chatMessageBlock'

Vue.component('chat-side-menu',chatSideMenu);
Vue.component('chat-side-menu-mobile',chatSideMenuMobile);
Vue.component('chat-block',chatBlockMessage);
export default {
  name: 'Chat',
  data () {
    return {
        picturesArray:[],
        clientArray:[],
        activeArray:[],
        typeArray:null,
        companion:{},
        pictureBot: {
          name:'Memes Bot',
          type:'pictures',
          image: 'https://media.licdn.com/mpr/mpr/AAEAAQAAAAAAAAwdAAAAJDZjNDMzZWFjLWNlZDItNDI1NC1iMDc2LTMyOGNmOWM4MTg1Mg.png'
        },
        yourClientBot: {
          name: 'Your Client',
          type:'client',
          image: 'https://frognews.bg/images/Ognyan_Stefanov/dreven_toiaga.jpg',
        },
        allUsers:[],
    }
  },
  mounted() {
    this.$root.$on('messagesArray',(event) =>{
      this.messeageBlock(event);
    });
    this.$root.$on('pushArray',(event) =>{
      this.addToArray(event);
    });
    this.allUsers=[this.pictureBot,this.yourClientBot];
  },
  methods: {
    messeageBlock(e) {
        switch (e.type) {
          case 'pictures' :
            this.activeArray=this.picturesArray;
          break;
          case 'family' :
            this.activeArray=this.familyArray;
          break;
          case 'client':
            this.activeArray=this.clientArray;
          break;
        }
        this.typeArray=e.type;
        this.companion=e.image;
    },
    addToArray(event){
      //console.log(event);
      switch (event.type) {
        case 'pictures' :
          this.picturesArray.push(event);
          break;
        case 'family' :
          this.familyArray.push(event);
          break;
        case 'client':
          this.clientArray.push(event);
          break;
      }
      //console.log(this.picturesArray,this.familyArray,this.clientArray);
    }
  }
}
</script>
<style>
@import '../css/Chat.css';
@import '../css/media.css';
</style>
