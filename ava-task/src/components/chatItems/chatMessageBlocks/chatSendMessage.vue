<template>
    <div class="Chat__sendblock" v-if="this.type!=null">
      <input type="text" ref="message" class="Messege__send" @keyup="anotherPlane()" @keyup.enter="sendMessage()" placeholder="Click here to write something...">
      <span @click="sendMessage()" ref="plane"><i  class="fa fa-paper-plane fa-2x"  ></i></span>
    </div>
</template>
<script>
  export default{
    props:['type'],
    methods: {
      anotherPlane(){

        if (this.$refs.message.value!='')
          this.$refs.plane.style.color='#5ac5c6';
        else
          this.$refs.plane.style.color='#000';
      },
      sendMessage() {
          let message={
            text:this.$refs.message.value,
            sender:'you',
            type:this.type,
          };
          this.$root.$emit('pushArray', message);
          this.botAnswer(message);
          this.$refs.message.value='';


      },
      botAnswer(message) {
        if (this.type=='pictures')
          this.pictureBot(message);
        else
          this.clientBot();
        this.$root.$emit('scrollDivBottom');
      },
      pictureBot(message){
        axios.get('https://pixabay.com/api/?key=3777400-917de2b0781e39fc4840d75c0&q='+message.text+'&image_type=photo')
          .then(
            res=> {
              //console.log(res.data.hits);
              let answer;
              let type;
              if (res.data.hits.length!=0) {
                answer=res.data.hits[0].previewURL;
                type='image';
              }
              else{
                answer='Sorry found nothing';
                type='text';
              }
              let botAnswer={
                text:answer,
                messageType:type,
                sender:'notYou',
                type:this.type,
              };
              this.$root.$emit('pushArray', botAnswer);
            }
          )
      },
      clientBot(){
        let answerArray=['Правки','Оно само сломалось','Подвиньте вон ту кнопку на 0.5px левее','У нас концепция поменялась','Ну и что , что Вы работаете за бесплатно за то это опыт', 'Я не мудак', 'Вы меня не понимаете!', 'Я что говорю на 對你來說不清楚的語言?' ];
        let index=Math.round(Math.random() * (answerArray.length-1 - 0) + 0);
        //console.log(index);
        let answer=answerArray[index];
        let botAnswer={
          text:answer,
          sender:'notYou',
          messageType:'text',
          type:this.type,
        };
        this.$root.$emit('pushArray', botAnswer);
      }
    }
  }
</script>
<style>

</style>
