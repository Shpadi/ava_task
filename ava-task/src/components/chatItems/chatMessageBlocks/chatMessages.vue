<template>
    <div ref="chatBlock" class="Chat__messagesblock">
        <div v-for="message in this.array">
            <div v-if="message.sender=='you'">
              <bubble-right :message="message"></bubble-right>
            </div>
            <div v-else>
              <bubble-left :message="message" :companionImg="companionImg"></bubble-left>
            </div>
        </div>
    </div>
</template>
<script>
  import Vue from 'vue';
  import bubbleLeft from './bubbles/chatBubbleLeft';
  import bubbleRight from './bubbles/chatBubbleRight';

  Vue.component('bubble-right',bubbleRight);
  Vue.component('bubble-left',bubbleLeft);
  export default{
    props:['array','companionImg'],
    mounted(){
      this.$root.$on('scrollDivBottom',(event) =>{
        this.scrollDiv(event);
      });
    },
    methods:{
      scrollDiv(event){
        let objDiv = this.$refs.chatBlock;
        //console.log(objDiv.scrollHeight);
        objDiv.scrollBy(0, objDiv.scrollHeight);
        //objDiv.scrollTop = objDiv.scrollHeight+1000;
      }
    }

  }
</script>
<style>

</style>
