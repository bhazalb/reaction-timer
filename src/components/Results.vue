<template>
<p> Reaction Time: {{ score }}</p>
<p class="rank">{{ rank }} </p>
</template>

<script>
 export default{
    props: ['score'],
    data() {
        return {
            rank: null
        }
    },
    mounted() {
        if(this.score <250){
            this.rank = 'Cool'
        } else if(this.score <400){
            this.rank = 'ehh :('
        }else{
            this.rank= 'slowly :((('
        }
    },
 }

</script>
<style>
.rank {
font-size: 1.4rem;
color: deeppink;
font-weight: bold;
}

</style>