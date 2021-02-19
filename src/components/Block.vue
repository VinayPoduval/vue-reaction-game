<template>
  <div class="block" v-if="showBlock" @click="stopTimer">
      Click Me!
  </div>
</template>

<script>
export default {
    props: ['delay'],
    data() {
        return {
            showBlock: false,
            startTime: null,
            endTime: null,
            timer: null,
            reactionTime: 0
        }
    },
    mounted() {
        setTimeout(()=>{
            this.showBlock = true
            this.startTimer()
        }, this.delay)
    },
    methods: {
        startTimer() {
            this.startTime = new Date()
            // this.timer = setInterval(()=>{
            //     this.reactionTime += 10
            //     if(this.reactionTime > 5000) {
            //         this.stopTimer()
            //     }
            // }, 10)
        },
        stopTimer() {
            this.endTime = new Date()
            this.$emit('end', this.endTime - this.startTime)
            // clearInterval(this.timer)
            // this.$emit('end', this.reactionTime)
        }
    }
}
</script>

<style>
    .block {
        width: 400px;
        border-radius: 20px;
        background: crimson;
        color: white;
        text-align: center;
        padding: 100px 0;
        margin: 40px auto;
        cursor: pointer;
    }

    @media screen and (max-width: 768px) {
        .block {
            width: 60%;
        }
    }
</style>