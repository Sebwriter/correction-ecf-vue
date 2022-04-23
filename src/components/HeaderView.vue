<template>
    <div id="header-wrapper">
      <div class="container">

        <!-- Header -->
        <header id="header">
          <div class="inner">

            <!-- Logo -->
            <h1><a href="index.html" >Magic</a></h1>
<router-link to="/"><h1>Magic</h1></router-link>
            <!-- Nav -->
            <nav id="nav">
              <ul>
                <li><router-link to="/">Home</router-link></li>
                <li><router-link :to="{name:'Collection'}">Ma Collection</router-link></li>
              </ul>
            </nav>
<slot name="aside"></slot>
          </div>
        </header>
        <slot name="banner"></slot>
        
      </div>
    </div>
</template>

<script>
export default {
    name:"HeaderView"
}
</script>