<template>
    <div  class="Chat__block">
      <chat-message-block :array="array" :companionImg="this.companionImg"></chat-message-block>
      <chat-message-send :type="type"></chat-message-send>
    </div>
</template>
<script>
  import  Vue from 'vue'
  import chatMessages from './chatMessageBlocks/chatMessages'
  import chatSendMessage from './chatMessageBlocks/chatSendMessage'

  Vue.component('chat-message-block',chatMessages);
  Vue.component('chat-message-send',chatSendMessage);
  export default {
        props: ['array','type','companionImg'],
        data() {
          return {}
        },
  }
</script>
<style>

</style>
