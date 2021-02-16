<template>
    <h2 v-if="score<=5000">Reaction time: {{score}}ms</h2>
    <h2 v-else>Failed! Try Again</h2>
    <p class="rank">{{rank}}</p>
</template>

<script>
export default {
    props: ['score'],
    data() {
        return {
            rank: null
        }
    },
    mounted() {
        if(this.score < 250) {
            this.rank = 'Woooohooo Ninja Fingers'
        }
        else if(this.score < 400) {
            this.rank = 'You\'re quick but not rapid'
        }
        else if(this.score < 5000) {
            this.rank = 'Eww Snail pace'
        }
    }
}
</script>

<style>
    .rank {
        font-size: 1.4em;
        color: crimson;
        font-weight: bold;
    }
</style>