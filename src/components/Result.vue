<template>
   <p>Reaction time: {{score}}ms</p>
   <p class="rank">{{rank}}</p>
   <p>Click Play to try again</p>
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
        if (this.score < 250) {
            this.rank = 'Sharp Guy!'
        } else if (this.score < 400) {
            this.rank = "You sef dey try."
        } else {
            this.rank = "Nawa for you"
        }
    }
}
</script>

<style>
    p{
        color: green;
        font-weight: bolder;
    }
</style>