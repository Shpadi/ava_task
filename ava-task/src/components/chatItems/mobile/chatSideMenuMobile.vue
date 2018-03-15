<template>

  <div class="Chat__sidebarmobile" ref="Chat__sidebarmobile">
    <div class="Chat__sidebarmobileblock"  v-for="user in this.allUsers" >
      <chat-sidemobile-item :type="type"  :user="user"></chat-sidemobile-item>
    </div>

  </div>
</template>
<script>
  import Vue from 'vue'
  import sideItem from '../mobile/chatSideItemMobile'


  Vue.component('chat-sidemobile-item',sideItem);
  export default{
    props:['type','allUsers'],
    data(){
      return {
        menuOpen:'',
      }
    },



  }
</script>
<style>

</style>
