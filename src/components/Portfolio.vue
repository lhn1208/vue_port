<template>
  <div class="container">
    <Header :activeTab="activeTab"  @update-active-tab="updateActiveTab" />
    <main class="main" id="main">
      <section class="sec portfolio_area contents_with">  
        <h2 class="fadeInLeft s1">PORTFOLIO</h2>
        <div class="tab_menu fadeInUp animated s1_4">
          <ul>
            <li><button :class="{ 'on': activeFilter === 'all' }" @click="filterItems('all')">All</button></li>
            <li><button :class="{ 'on': activeFilter === 'pc' }" @click="filterItems('pc')">Pc</button></li>
            <li><button :class="{ 'on': activeFilter === 'mobile'}" @click="filterItems('mobile')">Mobile</button></li>
            <li><button :class="{ 'on': activeFilter === 'p-m' }" @click="filterItems('p-m')">Pc/Mobile</button></li>
            <li><button :class="{ 'on': activeFilter === 'responsive' }" @click="filterItems('responsive')">Responsive</button></li>
          </ul>
        </div>
        <ul class="portfolio"><!-- fadeInUp animated s1_4-->
          <li v-for="item in portData" :key="item.title" :class="[item.device, { 'p-m': item.device === 'Pc/Mobile' }]">
            <article class="port_box">
              <a href="#">
                <figure class="img" :class="{ 'only_mb_img': item.only_mb_img }">
                  <img  v-if="item.pc_img" :src="item.pc_img" :alt="item.alt">
                  <span class="mb_img"><img v-if="item.mb_img" :src="item.mb_img" :alt="item.alt"></span>
                  <img v-if="item.only_mb_img" :src="item.only_mb_img" :alt="item.alt">
                </figure>
                <figcaption class="detail">
                  <h3><span>{{item.title}}</span></h3>
                  <ul class="desc">
                    <li>{{item.device}}</li>
                    <li>{{item.skill}}</li>
                    <li>{{item.date}}</li>
                  </ul>
                </figcaption>		
                
              </a>
            </article>
          </li>
        </ul>
      </section>
    </main>
  </div>
</template>
<script>
import data from "@/data";
import Header from '@/components/Header.vue';
export default {
  name: 'portMain',
  components: {
    Header
  },
  data() {
    return {
      portData: data,
      activeFilter: 'all', // 초기 필터링 값
      activeTab: 'portfolio', // activeTab 추가
    };
  },
  methods: {
    filterItems(filter) {
      this.activeFilter = filter;
      const portList = document.querySelectorAll('.portfolio>li');
      for (let pl of portList) {
        pl.style.display = 'none';
        
        if (pl.classList.contains(filter)|| filter === 'all') {
          pl.style.display = 'block';
        }
      }
      // const filteredCont = document.querySelectorAll(`.portfolio>li.${filter}`);
      
    },
    updateActiveTab(tab) {
      this.activeTab = tab;
    },
  },
};
</script>
<style>@import '../styles/style.css';</style>
<style scoped>
.main{padding-top: 100px;}
#main section h2{color:#000;}
.portfolio_area{padding-bottom:60px;}
.portfolio_area .tab_menu{margin-bottom: var(--content-pd); opacity: 0; animation-delay: .3s;}
.portfolio_area .tab_menu ul{display: flex; justify-content: center;}
.portfolio_area .tab_menu ul li{position: relative; margin: 6px;}
.portfolio_area .tab_menu ul li button{font-size: 14px; text-transform: uppercase; color:#000;}
.portfolio_area .tab_menu ul li button.on{position: relative; z-index: 2;}
.portfolio_area .tab_menu ul li button.on::after{position: absolute; bottom:2px; left: 0; width: 100%; height: 8px; background-color: rgba(238,163,3,.6); z-index: -1; content: "";}

.portfolio_area .portfolio{margin:0 auto; display: grid; grid-template-columns:repeat(3,33.3%); justify-content: center; row-gap:80px; /*opacity: 0;*/ animation-delay: .3s;}
.portfolio>li{position: relative; transition: width .4s ease;}
.portfolio>li .port_box a{display: block;}
.portfolio>li .img{position: relative; height: 272px; margin:0 auto; transition-duration: 0.5s;}
.portfolio>li .img img{width: 100%; height: 100%;}
.portfolio>li .mb_img{position: absolute; right:0; bottom: 0; width:30%; height: 80%; overflow: hidden;}
.portfolio>li .only_mb_img {text-align: center;}
.portfolio>li .only_mb_img img{width: auto; height: 272px;}
.portfolio .detail{margin-top: 30px; text-align: center;}
.portfolio>li .detail h3{position: relative; display: inline-block; margin-bottom: 10px;; font-size: 20px;}
.portfolio>li .detail h3 span{position: relative; z-index: 2; font-family: var(--body-font); text-transform: uppercase;}
.portfolio>li .detail h3:after{position: absolute; top:0; left:0; width: 0; height: 100%; background-color: var(--primary-color); transition: width .4s ease; -webkit-transition:width .4s ease; content: ""; z-index: 1;}
.portfolio .detail li{line-height: 2; font-size: 14px; text-transform: uppercase;}
.portfolio .detail li:nth-child(2){text-transform: uppercase;}
.portfolio>li:hover .img{transform:translate3d(0,-20px,0);}
.portfolio>li:hover .detail h3:after{width: 100%;}
/*태블릿 size*/
@media (max-width: 1024px){
  .contents_with, .content_skill h2{width: 100%;}
  .content_header::before,.content_header::after{border-width: 62px 25vw;} 
  /*Portfolio*/
  .portfolio_area{padding-bottom: var(--content-pd);}
  .portfolio_area .portfolio{grid-template-columns:repeat(2,1fr);}
  .portfolio>li .img{width: 84%; height: auto;}
  .portfolio .more_detail{margin-top: 0;}
}
@media (max-width: 767px){
  section h2{padding:20px; font-size: 26px;}
   /*Portfolio*/
  .portfolio_area h2{padding:30px 20px}
  .portfolio_area .portfolio{grid-template-columns:repeat(1,1fr); row-gap: 20px;}
  .portfolio_area .tab_menu{margin-bottom: 30px;}
  .portfolio_area .tab_menu ul li button{font-size: 12px;}
  .portfolio>li .img{width: 70%;}
  .portfolio>li:hover .img{transform:none;}
  .portfolio>li:hover .more_detail h3:after{width: 0;}
  .portfolio>li .more_detail h3 span{font-size: 14px;}
  .portfolio .more_detail li{font-size: 12px;}
  .portfolio .demo{height: 34px; font-size: 12px;}

}

</style>