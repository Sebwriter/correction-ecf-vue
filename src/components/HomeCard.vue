<template>
<div>
    <div class="col-4 col-12-medium">
        <section>
            <a href="#" class="image featured"><img :src="cartes[nbr].imageUrl" /></a>
            <header class="second icon solid fa-dragon">
                <h3>{{cartes[nbr].name}}</h3>
                <p>{{cartes[nbr].originalType}}</p>
            </header>
        </section>
    </div>
    </div>
</template>

<script>
import axios from 'axios'


export default {
    name: 'HomeCard',
    props:{
        nbr:{
            Type:Number
            
        }
    },
    data:()=>({
        cartes:[]
    }),
    

    async created() {
const lesCartes = await axios.get('https://api.magicthegathering.io/v1/cards')
this.cartes = lesCartes.data.cards
console.log(this.cartes)

    }
}
</script>