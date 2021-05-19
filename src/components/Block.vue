<template>
  <div class="block" v-if="showBlock" @click="stopTimer">
      Click Me
  </div>
  <div class="placeholder" v-if="!showBlock">
      Click the green box that will appear here as fast as you can.
  </div>
</template>

<script>
export default {
    name: 'Block',
    props: ['delay'],
    emits: ['end'],
    data() {
        return {
            showBlock: false,
            timer: null,
            reactionTime: 0
        }
    },
    mounted() {
        setTimeout(() => {
            this.showBlock = true
            this.startTimer()
        }, this.delay)
    },
    methods: {
        startTimer() {
            this.timer = setInterval(() => {
                this.reactionTime += 10
            }, 10)
        },
        stopTimer() {
            clearInterval(this.timer)
            this.$emit('end', this.reactionTime)
        }
    }
}
</script>

<style>
.block, .placeholder {
    width: 400px;
    border-radius: 20px;
    background: #0faf87;
    color: white;
    text-align: center;
    padding: 100px 0;
    margin: 40px auto;
}
.placeholder {
    background: white;
    color: black;
    border: 2px dashed black;
}
</style>