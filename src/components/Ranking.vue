
<template>

  <section id="ranking" style="margin-top: 86px;">
    <div class="cont_shop">
    <ul  class="list-inline text-center">
        <li v-for="(item, index) in menus" :key="index" class="list-inline-item" v-bind:class="item.classname"  @click="rankingMenu(index )">
        <a >{{item.title}}</a>
        </li>
    </ul>
    <div class="status_info"><span class="txt_notice">2019.9.27. 랭킹 업데이트</span></div>
    <ul class="list_shopinfo" id="infinite-list">
        <li  v-for="(item, index) in items" :key="index" >
          <a class="link_shopinfo ">
              <div class="sec">
              <span class="num_ranking">{{index+1}}</span>
              <span class="thumb_info" :alt="item.title">
                  <img :src="item.thum"  width="51" height="51" style="border-radius: 20px;"/>
              </span>
              </div>
              <div class="story_info sec">
              <span class="txt_info">{{item.title}}</span>
              <p class="desc_info">{{item.desc}}</p>
              </div>
          </a>
        </li>
    </ul>
</div>
    <component :is="dynamicComponent"></component>
  </section>
  
</template>
<script>
import axios from 'axios';
import Footer from './Footer.vue'
import Router from 'vue-router';

export default {
  components: {
    'app-footer':Footer
  },
  data() {
    return {
      menus: [
        { id: "all", title: "전체" ,classname:"on" },
        { id: "inpAge1", title: "10대" ,classname:""},
        { id: "inpAge2", title: "20대",classname:"" },
        { id: "inpAgeMan", title: "남성",classname:"" }
      ],
    currentIndx:0,
    axiosFlag: true,
    limit : 40,
    items: [],
    data: [],
    dynamicComponent: ''
    };
  },
  mounted () {
    if(  this.axiosFlag){
      // Detect when scrolled to bottom.
      window.addEventListener('scroll', e => {
                 let scrolledToBottom =
                document.documentElement.scrollTop + window.innerHeight ===
                document.documentElement.offsetHeight;
            if (scrolledToBottom) {
                this.isLoading = true;
                this.loadMore();
            }
      });
    }
    // Initially load some items.
    this.loadMore();
  
  },
  created: function() {
  },
  methods: {
    rankingMenu: function( index) {
       this.menus.map( x => {
            x.classname ='';
        });        
      this.menus[index].classname='on';
      this.axiosFlag  = true;
      this.currentIndx = index;
      this.loadMore();
    },
  loadMore () {
      this.loading = true;
      if( this.axiosFlag ){
        axios.get("../static/fakeapi"+this.currentIndx+".json").then(response => {  
          if(!this.data[this.currentIndx]){
                this.data[this.currentIndx] = [];
          }
          const total = response.data.length;
          const append = response.data.slice(
                this.data[this.currentIndx].length,
                this.data[this.currentIndx].length + this.limit
          );

          if( history.pushState ){
              history.pushState({mode:'',data:''}, "검색 결과", "?age="+ this.currentIndx );
          }

          this.data[this.currentIndx] =  this.data[this.currentIndx].concat(append);
          this.items =this.data[this.currentIndx] ;
          if(this.items.length >= total){
            this.axiosFlag = false;
            this.dynamicComponent = `app-footer`;
          }  
          this.loading = false;
      });
      }
    }

  }
};
</script>

<style>
#ranking{
    position: relative;
    overflow: hidden;
    min-height: 100vh;
    padding-bottom: 233px;
    -webkit-box-sizing: border-box;
    box-sizing: border-box;
    background-color: #fff;
}
.cont_shop {
    max-width: 710px;
    margin: 0 auto;
}
.list-inline {
    width: 100%;
    max-width: 331px;
    padding-top: 13px;
    margin: 0 auto;
}
.list-inline-item {
    width: 51px;
    height: 30px;
    margin: 0 auto;
    border-radius: 15px;
    font-size: 15px;
    color: #888;
    line-height: 32px;
    text-align: center;
}
.list-inline-item.on {
    color: #fff;
    background-color: #000;
}
/* ranking list */
.sec { display: table-cell; vertical-align: middle;}
.cont_shop .status_info {
    position: relative;
    height: 55px;
    padding-left: 22px;
}
.cont_shop .status_info .txt_notice {
    display: block;
    padding-top: 30px;
    font-size: 11px;
    color: #adadad;
}

.list_shopinfo {border-top: 1px solid #f5f5f5;}
.list_shopinfo li {list-style: none;  border-bottom: 1px solid #f5f5f5; }
.link_shopinfo {
    display: table;
    position: relative;
    height: 70px;
}
.story_info {
    padding: 10px 72px 0 20px;
}

.num_ranking {
    display: inline-block;
    margin-top: -10px;
    font-size: 15px;
    color: #777;
    width: 45px;
    text-align: center;
}
#ranking .desc_info {
    width: 200px;
    margin-top: 3px;
    font-size: 13px;
    line-height: 15px;
    color: #b3b3b3;
}   

.list_shopinfo .link_shopinfo .desc_info,  .list_shopinfo .link_shopinfo .txt_info {
    max-width: 100%;
    font-weight: 400;
    word-break: break-all;
    -o-text-overflow: ellipsis;
    text-overflow: ellipsis;
    white-space: nowrap;
    overflow: hidden;
}


</style>
