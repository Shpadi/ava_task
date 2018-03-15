<template>
    <div class="bubbleRight">
      <span class="Chat__text">{{this.message.text}}</span>
      <img class="Chat__avatar" src="https://d30y9cdsu7xlg0.cloudfront.net/png/363633-200.png">
    </div>
</template>
<script>
    export default {
      props:['message'],
    }
</script>
<style>

</style>
