<template>
    <div class="container">
        <Header :activeTab="activeTab" :whiteType="true" @update-active-tab="updateActiveTab" /><!--Header 컴포넌트(자식)에 whiteType속성을 동적으로 전달-->

        <div class="contetn_width">
          <section class="sec content_skill">
            <div class="stars_wrap">
              <img class="stars stars-animation" src="@/assets/background.png" alt="">
              <img class="stars stars-animation-two" src="@/assets/background.png" alt="">
              <img class="stars stars-animation-three" src="@/assets/background.png" alt="">
            </div>
            <h2>SKILL</h2>
            <div class="skill_area contents_with">
              <ul class="skill_list">				
                <li>
                  <div class="front s1"><span>HTML5/CSS3/SASS</span></div>
                  <div class="back"><span>W3C에 준수하는 웹표준</span></div>
                </li>
                <li>
                  <div class="front s1_4"><span>Jquery/Javascript</span></div>
                  <div class="back"><span>스크립트<br>동작 구현</span></div>
                </li>
                <li>
                  <div class="front s1_6"><span>반응형웹</span></div>
                  <div class="back"><span>전 기기 반응하는<br>반응형</span></div>
                </li>
                <li>
                  <div class="front s1_8"><span>웹접근성</span></div>
                  <div class="back"><span>모두 접근 가능한<br>접근성</span></div>
                </li>
              </ul>
            </div>
          </section>
          <!--about-->
          <section class="sec content_about" id="basic-waypoint">
            <h2>ABOUT</h2>
            <div class="about_area">
              <h3>My Info</h3>
              <ul class="about animated s1">
                <li><strong>Name:</strong>&nbsp;이 하 나</li>
                <li><strong>Email:</strong>&nbsp;lhn1208@naver.com</li>
                <li class="tools"><strong>Tools:</strong>&nbsp;VsCode/Git/figma/<span class="mb-block">/Websquare</span></li>
              </ul>	
              <h3>Career</h3>
              <ul class="about animated s2">
                <li><strong>ITANS</strong>/IT Company</li>
                <li><strong>온앤온정보시스템</strong>/IT Company</li>
                <li><strong>애드캡슐소프트</strong>/Web Agency</li>
                <li><strong>모두투어</strong>/Travel Company</li>
                <li><strong>IDS&amp;Trust</strong>/Dawoong Group</li>
              </ul>
            </div>
          </section>
          <!--//about-->
        </div>
    </div>
</template>
<script>
import Header from '@/components/Header.vue';
export default {
  name: 'portAbout',
  components: {
    Header
  },
  data() {
    return {
      activeTab: 'about', // activeTab 추가
    };
  },
  mounted() {
      console.log('about vue');
    this.$parent.activeTab = 'about';
    const skillList=document.querySelectorAll('.skill_list .front');
    for (let sl of skillList) {
       sl.classList.add('bounce', 'animated');
        sl.style.opacity = 1;
    }
  },
  updateActiveTab(tab) {
    alert();
    this.activeTab = tab;//about을 클릭하면 인자가 about->this.activeTab
    console.log('about의 updateActiveTab', this.activeTab )
  },
}
</script>
<style>@import '../styles/style.css';</style>
<style scoped>
/*skill*/
.content_skill{position: relative; padding-top: 100px; padding-bottom: 2.5rem; background: linear-gradient( to top, #5e1530, #152944 );}
.content_skill .stars_wrap{position: absolute; width: 100%; height: 100%; top:0; bottom: 0; left: 0; overflow: hidden;}
.content-skill .stars_wrap .stars{position: absolute; width:100%; height: 100%; top:0; left: 0; opacity: 0;}
.stars-animation{animation:stairs 9s linear infinite;}
.stars-animation-two{animation:stairs 9s linear infinite; animation-delay: 3s;}
.stars-animation-three{animation:stairs 9s linear infinite; animation-delay: 6s;}
.content_skill h2{width: 100%; max-width: 1200px; margin:0 auto; color: var(--white-color); }
.skill_area{text-align: center; margin:20px auto;}
.skill_area .skill_list{display: flex;}
.skill_area .skill_list li{width:25%; height: 210px; padding-bottom: var(--content-pd); cursor: pointer; position: relative;}
.skill_area .skill_list li>div{display: table; width: 210px; height: 210px; border-radius: 50%; font-size: 1.5rem; text-align: center; color:var(--white-color); background: rgba(255,255,255,0.1); transition: all .5s ease-out 0s;}
.skill_area .skill_list li>div span{display: table-cell; vertical-align: middle;}
.skill_area .skill_list li .front{transform: rotateY(0deg); opacity: 0;}
.skill_area .skill_list li .back{position: absolute; top:0; left: 0;  color:#111; background-color: var(--white-color); transform: rotateY(-180deg); opacity: 0;}
.skill_area .skill_list li:hover .front{transform: rotateY(-180deg); opacity: 0;}
.skill_area .skill_list li:hover .back{transform: rotateY(0deg); opacity: 1;}
.skill_area .skill_list li:hover .back:after{position: absolute; top: -7px; left: -7px; width: 100%; height: 100%; padding: 7px;border-radius: 50%; box-shadow: 0 0 0 4px var(--white-color); content: '';} 
/*About*/
.content_about{background:#161717; text-align: center; position: relative;}
.content_about h2{color: var(--white-color); padding-bottom: var(--content-pd);}
.content_about .about_area h3{margin-bottom: 20px; color: var(--white-color); font-size: 1.875rem;}
.about_area .about{width: 450px; margin:0 auto; padding-bottom: 30px;}
.about_area .about .act2{visibility: hidden; animation-delay: 0.2s; animation-name: none}
.about_area .about li{margin-bottom: 15px; padding:15px; background-color: var(--white-color); border-radius: 50px; font-size:1rem; text-transform: uppercase;}
@media (max-width: 1024px){
    /*Skill*/
  .skill_area .skill_list{flex-wrap:wrap;}
  .skill_area .skill_list li{width: 50%;}
  .skill_area .skill_list li>div{margin:0 auto;}
  .skill_area .skill_list li>div span{font-size: 16px;}
  .skill_area .skill_list li .back{left: 27%;}
  /*about*/
  .text_ico_ev{display: none;}
}
/*모바일 size*/
@media (max-width: 767px){ 
   /*Skill*/
  .content_about h2{padding-bottom: 20px;}
  .content_skill{padding-bottom: .5rem;}
  .skill_area .skill_list li{width: 100%; height: auto; padding-bottom: 24px;}
  .skill_area .skill_list li>div{width: 160px; height: 160px; margin: 0 auto 16px;}
  .skill_area .skill_list li>div span{font-size: 14px;}
  .skill_area .skill_list li:hover .front{transform: rotateY(0deg);}
  .skill_area .skill_list li:hover .back{display: none;}
  /*About*/
  .content_about .about_area h3{font-size: 22px;}
  .about_area .about{width: 300px; padding-bottom: 16px;}
  .about_area .about li{padding:8px; font-size: 12px;}
  .footer{font-size: 14px;}
}
</style>