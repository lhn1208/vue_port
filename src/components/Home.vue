<template>
  <main class="home_main">
    <div class="title animated fadeInLeft s1">Web
      <div class="message_wrap"> 
        <div class="message">
            <div>Coding</div>
            <div>Creating</div>
            <div>Publisher</div>
        </div>
      </div>
      <div class="mb">Publisher</div>
    </div>
    <div class="bg_wrap">
      <span class="img type1"><img src="@/assets/doctor.png"></span>
      <span class="img type4"><img src="@/assets/bank_bottom.png"></span>
      <span class="img type2"><img src="@/assets/home1.png"></span>
      <span class="img type3"><img src="@/assets/travel.png"></span>
    </div>
     <button class="btn" @click="togoPort">
        <span class="text">메인으로 가기</span>
      <span class="line1"></span><span class="line2"></span><span class="line3"></span><span class="line4"></span>
      </button> 
    <!-- <div class="lock" @click="toggleLock"></div> -->
  </main>
</template>

<script>
export default {
  name: 'portHome',
  data(){
      return {
        };
  },
  mounted() {
  },
  methods: {
     togoPort(){
      this.$router.push({
        path: "Portfolio"
      })
    },
  }
}
</script> 
<style>@import '../styles/style.css';</style>
<style scoped>
.home_main{position:relative; height:100vh; background: #000; overflow: hidden;}
.home_main .title, .btn{margin-left: 200px;}
.home_main .title{position: relative; margin-top: 180px;  color: #fff; font-size: 102px; font-weight: bold; z-index: 10; opacity: 0;}
.message_wrap{position: relative; overflow: hidden; height: 130px; text-transform: uppercase; white-space: nowrap; color: #333;font-size: 48px; font-weight: 100;line-height: 1.5;}
.message {display: block; position: absolute; top: 12.5rem; overflow: hidden; color: #fff; font-size: 6.25rem; background-color: var(--primary-color);
  -webkit-animation: openclose 5s ease-in-out infinite; animation: openclose 5s ease-in-out infinite;}
.message div{padding-left: 14px; font-size: 80px; font-family: var(--body-font);}
.bg_wrap{position: relative;}
.bg_wrap .img{display: inline-block; position: absolute; /*opacity:1; animation:fadeDiagonal forwards .4s; */right: -100%; bottom: -100%; transform: rotate(-45deg); animation-fill-mode: forwards; transition: ease; opacity: 0;}
.bg_wrap .type1{/*right: 322px; bottom: -290px;*/ animation-name: fadeDiagonal1; animation-duration: 1s;}
.bg_wrap .type2{/*right: -180px; bottom: 290px*/ animation-name: fadeDiagonal2; animation-duration: 3s;}
.bg_wrap .type3{/*right: -278px; bottom: -354px;*/ animation-name: fadeDiagonal3; animation-duration: 2.4s;}
.bg_wrap .type4{/*right: 288px; bottom: 218px*/ animation-name: fadeDiagonal4; animation-duration: 2s;}
.btn{display: block; position: relative; margin-top:20px; font-size: 20px; color: #fff; border:1px solid #fff; z-index: 10;}
.btn .text{display: block; padding: 10px 20px; background: transparent; box-sizing: border-box;}
.btn *[class*="line"]{position: absolute; display: block; background-color: var(--primary-color); transition: all .4s ease;}
.btn .line1{top: 0; width: 0; height: 1px; }
.btn .line2{top: 0; right: 0; width: 1px; height:0; }
.btn .line3{bottom: 0; right: 0; width: 0; height: 1px; }
.btn .line4{bottom: 0; left: 0; width: 1px; height:0;}
.btn:hover{border:0;}
.btn:hover .line1{width:100%}
.btn:hover .line2{height:100%;}
.btn:hover .line3{width:100%;}
.btn:hover .line4{height:100%;}
@media screen and (max-width: 1440px) {
 /* .bg_wrap .img{width:50%} */
 .home_main .title{color: var(--primary-color);}
 .home_main .bg_wrap::before{content: ""; position: fixed; top:0; left:0; right:0; bottom:0; background-color: rgba(0,0,0,.7); z-index: 2;}
}
@media screen and (max-width: 1024px) {
  .bg_wrap .type1,.bg_wrap .type4{display: none;}
}
@media (max-width: 767px){
.home_main .title, .btn{margin-left: 40px;}
.home_main .title{padding-top: 100px; font-size: 50px;}
.btn{font-size: var(--mb-font-size);}
.message_wrap{display: none;}
/* .bg_wrap .img{width:100%} */
.bg_wrap .type1{right:-274px; bottom: -882px; display: block; opacity: 1; animation: none;}
}
@media (max-width: 480px){
  .bg_wrap .type3{animation-name: fadeDiagonal3_mb;}
/* .bg_wrap .type1{right:-274px; bottom: -834px; display: block; opacity: 1; animation: none;} */
}


</style>

