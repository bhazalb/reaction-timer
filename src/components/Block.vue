<template>
    <div class="block"  v-if="showBlock"  @click="stopTimer">
        click me
    </div>
</template>

<script>
export default {
    props: ['delay'],
    data() {
        return {
            showBlock: false,
            timer : null ,
            reactionTime : 0,
        }
    },
    /* lifecycle hooks (yaşam döngüsü konusu) play a basıncs mounted çalıştı */
    mounted () {
        console.log('component mounted')
        setTimeout(() => {
            this.showBlock = true
            this.startTimer()
        }, this.delay);
    }, 
    /* mounted çalıştıktan sonra çıkan gri ekranda da updated çalıştı */ 
    /*updated() {
        console.log('component update')
    },*/

    methods: {
        startTimer(){
         this.timer = setInterval(() => {
            this.reactionTime += 10
         }, 10)
        },
        stopTimer (){
        clearInterval (this.timer)
        this.$emit('end', this.reactionTime)
        }
    }
}
</script>

<style>
.block{
width: 400px;
border-radius: 20px;
background-color: rgb(67, 91, 95);
color: white;
text-align: center;
padding: 100px 0;
margin: 40px auto;
}


</style>
