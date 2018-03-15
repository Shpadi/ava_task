<template>
  <div class="bubbleLeft">
    <img class="Chat__avatar" :src="this.companionImg">
    <img v-if=" this.message.messageType=='image'"  :src="this.message.text">
    <span v-else  class="Chat__text">{{this.message.text}}</span>

  </div>
</template>
<script>
  export default {
    props:['message','companionImg'],
  }
</script>
<style>

</style>
