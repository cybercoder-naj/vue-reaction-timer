<template>
  <p>Reaction Time: {{ score }} ms</p>
  <p class="rank">{{ rank }}</p>
</template>

<script>
export default {
    name: 'Rank',
    props: ['score'],
    data() {
        return {
            rank: null
        }
    },
    mounted() {
        this.rank = (this.score < 250) ?
            "Super Fast like Flash!!"
        : (this.score < 400) ?
            "Quick like Quick Silver!"
        : "Slow as a Snail..."
    }
}
</script>

<style>
.rank {
    font-size: 1.4em;
    color: #0faf87;
    font-weight: bold;
}
</style>