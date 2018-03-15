<template>
  <div class="Chat__sidebaritemmobile" @click="showMessages()">
    <img :src="user.image">
  </div>
</template>
<script>
  export default {
    props:['user'],
    methods:{
      showMessages() {
        this.$root.$emit('messagesArray', this.user);
      }
    }
  }
</script>
<style>

</style>
