<template>
  <div class="block" v-if="showBlock" @click="stopTimer">
      Click me
  </div>
</template>

<script>
export default {
    props: ['delay'],
    data(){
        return{
            showBlock: false,
            timer: null,
            reactionTime: 0
        }
    },
    mounted(){
        setTimeout(() => {
            this.showBlock = true
            this.startTimer()
        }, this.delay) 
    },
    updated(){
        console.log('Component Updated')
    },
    unmounted(){
        console.log('unmounted')
    },
    methods: {
        startTimer (){
            this.timer = setInterval(() => {
                this.reactionTime += 10
            }, 10)
        },
        stopTimer() {
            clearInterval(this.timer)
            console.log(this.reactionTime)
        }
    }
}
</script>

<style>
    .block{
        width: 400px;
        border-radius: 10px;
        background: teal;
        color: rgb(140, 161, 161);
        text-align: center;
        padding: 100px 0;
        margin: 40px auto;
    }
</style>