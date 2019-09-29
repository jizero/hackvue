<template>
  <div id="app">
    <div class="ly_wrapper">
    <app-nav-bar></app-nav-bar>
    <app-ranking></app-ranking>
    </div>
  </div>
</template>

<script>
import Banner from './components/Banner.vue'
import NavBar from './components/Navbar.vue'
import Ranking from './components/Ranking.vue'


export default {
  name: 'App',
  components: {
    appBanner: Banner,
    appRanking: Ranking,
    appNavBar: NavBar
  }
}
</script>

<style lang="scss">
  @import './styles/custom_bootstrap.scss';
  @import '../node_modules/bootstrap/scss/bootstrap.scss';
</style>

<style>
ul { margin: 0; padding:0;}
body {
  margin-top: 60px;
}
h1, h2, h3, h4, h5 {
    font-family: Apple SD Gothic Neo,Apple SD Gothic,Apple Gothic,Malgun Gothic,"\B9D1\C740 \ACE0\B515",sans-serif;
}

.navbar {  max-width: 750px; margin: 0 auto;}
.ly_wrapper  {margin: 0 auto;}
.navbar-brand {
  width:100%;
}
.nav-item {
    float: left;
    width: 25%;
    height: 100%;
    border-bottom: 1px solid rgba(34,34,34,.1);
}    
</style>