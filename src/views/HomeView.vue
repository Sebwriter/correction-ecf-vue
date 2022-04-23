<template>
  <div class="home">
    <HeaderView>
      <template v-slot:banner><div id="banner">
								<h2><strong>Magic Card:</strong> Ma collection </h2>
							</div>
              </template>
              <template v-slot:aside><div id="banner">
								<h2><strong>Magic Pokemon:</strong> Pikachu</h2>
							</div>
              </template>
              </HeaderView>
<div id="main-wrapper">
					<div class="wrapper style1">
						<div class="inner">

							<!-- Feature 1 -->
								<section class="container box feature1">
									<div class="row">
										<div class="col-12">
											<header class="first major">
												<h2>Mes 3 Dernières Cartes</h2>
											</header>
										</div>
										<HomeCard 
                    :nbr="cartes.length-1" />
                    <HomeCard 
                    :nbr="cartes.length-2" />
                    <HomeCard 
                    :nbr="cartes.length-3" />


									</div>
								</section>

						</div>
					</div>
				</div>
  </div>
</template>

<script>
// @ is an alias to /src
import HeaderView from '@/components/HeaderView.vue'
import HomeCard from '@/components/HomeCard'
import axios from 'axios'

export default {
  name: 'HomeView',
  components: {
    HomeCard,
    HeaderView
  },
  data:()=>({
        cartes:[]
    }),
  async created(){
    const lesCartes = await axios.get('https://api.magicthegathering.io/v1/cards')
    this.cartes=lesCartes.data.cards
    console.log(this.cartes)
    console.log(this.cartes.length)
  }
}
</script>
