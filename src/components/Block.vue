<template>
  <div class="block" v-if="showBlock" @click="clearTimer">
    <h1>Block</h1>
  </div>
</template>

<script>
export default {
    props : ['delay'],
    data(){
        return {
            showBlock : false,
            timer : null,
            reactionTime : 0
        }
    },
    mounted(){
        console.log('The block is here')
        setTimeout(() => {
            this.showBlock = true
            this.startTimer()
            // console.log(this.delay)
        },this.delay)
    },
    methods : {
        startTimer(){
            this.timer = setInterval(() => {
                this.reactionTime += 10
            },10)
        },
        clearTimer(){
            clearInterval(this.timer)
            console.log(this.reactionTime)
            this.$emit('end',this.reactionTime)
        }
    }
};
</script>
<style lang="sass" scoped >
.block
    height: 300px
    width: 300px
    margin: 10px auto 
    border-radius: 30px
    background-color: black
    display: flex
    align-items: center
    justify-content: center
    h1
        color: white
        font-size: 50px
</style>>
