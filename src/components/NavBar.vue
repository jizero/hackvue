<template>
<header class="fixed-top bg-light">
  <nav class="navbar" style="padding-bottom:0;">
    <a href="#" class="navbar-brand text-center">kakao<strong>Style</strong></a>
    <div id="navbarBrand" class="navbar-collapse justify-content-end">
      <ul class="nav justify-content-center">
        <li v-for="(mn , index) in navmenus" :key="index" class="nav-item" >
          <a :href="mn.id" v-bind:class="{'nav-link text-uppercase':true ,  'on':(mn.id === '#shop')}">{{mn.title}}</a>
        </li>
      </ul>
    </div>
  </nav>
</header>  
</template>
<script>
export default {
  data() {
    return {
      navmenus: [
        { id: "#hot", title: "hot" },
        { id: "#sale", title: "sale" },
        { id: "#soho", title: "soho" },
        { id: "#shop", title: "shop" }
      ]
    };
  }
};
</script>
<style >
.nav-link{
    font-size: 14px;
    color: #999;
    text-align: center;
}
.nav-link.on {
    font-weight: 700;
    color: #000;
    border-bottom: 2px solid #000;
    margin-bottom: -2px;
}
</style>
