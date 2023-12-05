
<template>
  <navbar :pages="navigation" :selected_page="selected_item" :clickLinkNavbar="(index) => selected_item = index" />
  <WebView :pages="navigation" :select="selected_item" :creagePage="creagePage" />
</template>

  <script>
    import navbar from './components/navbar.vue';
    import WebView from './components/webView.vue'

    export default {
      components : {
        navbar, WebView
      },
      data() {
        return {
            navigation: [],
            selected_item: 0
        };
    },
    created(){
        this.getPages();
        setTimeout(() => console.log("app.vue navigation : "+ this.navigation), 3000);
        
    },
    methods:{
        async getPages (){
            let res = await fetch('/pages.json');
            let data = await res.json();
            console.log("app.vue data : "+ data);
            this.navigation = data;
        },

        creagePage(pageObject){
          console.log("this is from app.vue file :smily-face :"+JSON.stringify(pageObject))
          this.navigation.push({
            "name": pageObject.firstname,
            "href": "#",
            "current": false,
            "publish":true
          });

          console.log(this.navigation);
        }
    }
    }
    
  </script>

<style scoped>

</style>
