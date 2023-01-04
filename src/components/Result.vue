<template>
  <h1>Reaction Time: {{score}} ms</h1>
  <p>{{rank}}</p>
</template>

<script>
export default {
    props: ['score'],
    data(){
        return{
            rank: null,
        }
    },
    mounted(){
        if(this.score < 200){
            this.rank='Ninja Finger'
        } else if (this.score < 400){
            this.rank = 'You are Slower'
        } else {
            this.rank = 'Snail pace'
        }
    }
}
</script>

<style>

</style>