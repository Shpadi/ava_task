<template>

    <div class="Chat__sidebar" ref="Chat__sidebar">
      <div class="Chat__sidebarblockmobile"  v-for="user in this.allUsers" >
        <chat-side-item :type="type"  :user="user"></chat-side-item>
      </div>

    </div>
</template>
<script>
  import Vue from 'vue'
  import sideItem from './chatSideItem'


  Vue.component('chat-side-item',sideItem);
  export default{
    props:['type','allUsers'],

  }
</script>
<style>

</style>
