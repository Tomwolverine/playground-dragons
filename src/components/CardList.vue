<template>
    <div>
        <Card v-for="dragon in dragons" :key='dragon.id' :dragon="dragon"/>
    </div>
</template>

<script>
import Card from './Card'
export default {
    name: "CardList",
    components: { 
        Card
        },
data(){
    return {
        dragons: null
        }
    },
    methods: { 
        fetchDragons() {
            fetch('../../static/dragons.json')
                .then((response) => response.json())
                .then((response) => this.dragons = response.dragons)
                .then(() => console.log(this.dragons, 'data'))
                
        }

    },
    mounted() {
        this.fetchDragons() 
        // this.$nextTick()
        
    }
}

</script>

<style>

</style>
