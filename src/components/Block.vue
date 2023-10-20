<template>
    <div class="block"  v-if="showBlock">
        click me
    </div>
</template>

<script>
export default {
    props: ['delay'],
    data() {
        return {
            showBlock: false
        }
    },
    /* lifecycle hooks (yaşam döngüsü konusu) play a basıncs mounted çalıştı */
    mounted () {
        console.log('component mounted')
        setTimeout(() => {
            this.showBlock = true
            console.log(this.delay)
        }, this.delay);
    }, 
    /* mounted çalıştıktan sonra çıkan gri ekranda da updated çalıştı */ 
    updated() {
        console.log('component update')
    },
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
