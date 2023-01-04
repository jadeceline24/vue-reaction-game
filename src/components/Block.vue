<template>
  <div class="block" v-if="showBlock" @click="stopTimer">
    CLICK ME
  </div>
</template>

<script>
export default {
    props: ['delay'],
    data(){
        return {
            showBlock:false,
            timer: null,
            reactTime: 0
        }
    },
    mounted(){
        setTimeout(() => {
            this.showBlock = true
            this.startTimer()
        }, this.delay)
    },
    methods: {
        startTimer(){
            this.timer = setInterval(() => {
                this.reactTime += 10
            }
            , 10)
        },
        stopTimer(){
            clearInterval(this.timer)
            this.$emit('end', this.reactTime) //storing in end
        }
    },
}
</script>

<style>
    .block {
        width: 400px;
        background: red;
        text-align: center;
        margin: 40px auto;
        padding: 100px 0;
    }
</style>