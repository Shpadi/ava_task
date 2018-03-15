<template>
    <div :class="activeClass" ref="Chat__sidebaritem"   @click="showMessages()">
      <img :src="user.image"> <p>{{user.name}}</p>
    </div>
</template>
<script>
  export default {
    props:['type','user'],
    computed: {
      activeClass() {
        if (this.type==this.user.type)
          return 'Chat__sidebaritem active'
        else
          return 'Chat__sidebaritem'
      },


    },
    methods:{

      showMessages() {
        this.$root.$emit('messagesArray', this.user);

      }
    }
  }
</script>
<style>

</style>
