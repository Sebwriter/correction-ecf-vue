<template>
<div>
    <HeaderView />
    <div id="main-wrapper">
					<div class="wrapper style2">
						<div class="inner">
							<div class="container">
								<div class="row">
									<div class="col-8 col-12-medium">
										<div id="content">

											<!-- Content -->

												<article>
													<header class="major">
														<h2>{{carte.name}}</h2>
														<p>{{carte.artist}}</p>
													</header>

													<span class="image featured">
														<img :src="carte.imageUrl" alt="" />
													</span>

													<p>{{carte.text}}</p>
												</article>

										</div>
									</div>
									<div class="col-4 col-12-medium">
										<div id="sidebar">

											<!-- Sidebar -->

												<section>
													<header class="major">
														<h2>Infos</h2>
													</header>
													<p>set name: <b>{{carte.setName}}</b></p>
													<p >rarity:  <b>{{carte.rarity}}</b></p>
													<p >toughness:  <b>{{carte.toughness}}</b></p>

													<span class="button alt icon ">
														{{'Card power ' + power}}
													</span>
												</section>
										</div>
									</div>
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
    name: 'HomeCard',
    components:{
HeaderView
    },
    
    data:()=>({
        carte:{},
        power:""
    }),
    

    async created() {
        const {cardId} = this.$route.params
const laCarte = await axios.get('https://api.magicthegathering.io/v1/cards/' + cardId)
this.carte = laCarte.data.card
console.log(this.carte)

for(let i=0;i<this.carte.power;i++) {
    this.power= this.power+'🔥'
}
if (this.power == "") { this.power = ": None" }
    }
}
</script>
