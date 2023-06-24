<template>
   <header :class="headerClasses">
      <div class="contents_with">
        <h1 class="logo"><a href="#"><img src="@/assets/logo_myport.png" alt="my portfolio 로고"></a></h1>
        <nav>
            <button :class="{ 'active': this.activeTab === 'home' }" @click="togoHome">Home</button>
            <button :class="{ 'active': this.activeTab === 'portfolio' }" @click="togoPort()">Portfolio</button>
            <button :class="{ 'active': this.activeTab === 'about' }" @click="togoAbout()">About Me</button>
        </nav>
      </div>
    </header>
</template>

<script>
export default {
    name: 'portHeader',   
    props: {
        whiteType: Boolean,
    },
    computed: {
         headerClasses(){
            return{
                'header': true,
                'white_type': this.whiteType === true,
            };
         },
    },
    mounted() {
        console.log('header vue')
        console.log('-->this.activeTab', this.activeTab);
        this.$nextTick(() => {
            window.addEventListener('scroll', this.handleScroll);
        });
    },
    beforeUnmount() {
        window.removeEventListener('scroll', this.handleScroll);
    },
    data() {
        return {
            activeTab: 'portfolio'
        };
    },
    methods: {
         togoHome() {
            this.$emit('update-active-tab', 'home'); // 이벤트 발생
            this.$router.push({ path: '/' });
        },
        togoPort() {
        this.$emit('update-active-tab', 'portfolio'); // 이벤트 발생
        this.$router.push({ path: 'Portfolio' });
        },
        togoAbout() {
            this.$emit('update-active-tab', 'about'); // 이벤트 발생
            this.$router.push({ path: 'About' });
              console.log('togoAbout');
            // .then(() => {
            //     this.activeTab = "about";
                
            // });
        },
        handleScroll() {
             const header = document.querySelector('.header');
            let scrollPos = document.documentElement.scrollTop;
            if (scrollPos > 0) {
                header.classList.add('fixed');
            } else {
                header.classList.remove('fixed');
            }
        }
    },
 
}
</script>
<style scoped>
/*Header*/
.header{position: fixed; top:0; left: 0; bottom: 0; right:0; height: 100px; transition: box-shadow .4s ease-in-out; z-index: 90; border-bottom: 1px solid #bbb;}
.header.fixed{background-color: rgba(255,255,255,.4); box-shadow: 0 6px 10px -5px #d6d6d6; border-bottom: none;}
.header.white_type{background-color: rgba(255,255,255,.4);}
.logo{position: absolute; top: 14px; left: var(--content-pd); z-index: 90;}
.logo a{display: block; width: 188px; transition: width .3s ease-in;}
.header nav{display: flex; justify-content: flex-end; align-items: center; gap: 16px; height: 100px;}
.header nav button{font-size: 18px; color: #000; text-transform: uppercase; font-weight: bold;}
.header nav button.active{color: var(--primary-color);}
@media (max-width: 767px){ 
    /*Header*/
  .logo{left: 14px;}
  .logo a{width: 120px;}
  .content_header .tit{font-size: 50px;}
  .content_header .message_wrap{display: none;}
  .content_header .tit .mb{opacity: 1; transition: all .4s;}
  .logo{background-position-x: 42%; background-size: 255% 100%;}
  .header nav button{font-size: var(--mb-font-size)}
}
</style>