<template>
<div>
    <HeaderView />
    <div id="main-wrapper">
        <div class="wrapper style2">
            <div class="inner">
                <div class="container">
                    <div id="content">

                        <!-- Content -->

                        <article >
                            <header class="major">
                                <h2>Ma Collection</h2>
                            </header>
                            <div class='card-list' v-for="(carte,idx) in cartes" :key="idx">
                                <div class='card-title'><b>{{'# '+(idx+1)}}</b> {{carte.name}}</div>
                                <div class='card-action'
                                @click="goToSelectedCard(carte.id)"><a href='#'>👀</a></div>
                            </div>

                        </article>

                    </div>
                </div>
            </div>
        </div>

    </div>
    </div>
</template>

<script>
import axios from 'axios'
import HeaderView from '@/components/HeaderView.vue'

export default {
    name: 'CollectionView',
components:{
    HeaderView
},

    data: () => ({
        cartes: []
    }),
    methods:{
goToSelectedCard(id){
    this.$router.push({name:'CardDetails', params:{cardId:id}})
}
    },
    async created() {
        const lesCartes = await axios.get('https://api.magicthegathering.io/v1/cards')
        this.cartes = lesCartes.data.cards
        console.log(this.cartes)

    }
}
</script>

<style scoped>
@import url(@/assets/css/card-list.css);
</style>