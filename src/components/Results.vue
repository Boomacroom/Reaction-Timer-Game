<template>
  <p class='rank'>Reaction Time: {{ result }} ms<br>{{rank}}!</p>
</template>

<script>
export default {
    props: [
        'result'
    ],
    data() {
        return {
            rank: null
        }
    },
    mounted() {
        if (this.result < 250){
            this.rank = 'Ninja Fingers'
        } else if (this.result < 350){
            this.rank = 'Rapid Reflexes'
        } else if (this.result < 450){
            this.rank = 'Snails Pace'
        } else if (this.result > 451){
            this.rank = 'Check Your Pulse!'
        } 
    }

}
</script>

<style scoped>
.rank {
    color: green;
    font-weight: 600;
    font-size: 2em;
}
</style>