<template>
  <div id="app">
    <Chat/>
  </div>
</template>

<script>
import Vue from 'vue'
import Chat from './components/Chat'

Vue.component('Chat',Chat);
export default {
  name: 'App',

}
</script>

<style>
  @import "css/style.css";
</style>
