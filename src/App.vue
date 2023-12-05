
<template>
  <navbar :pages="publishPage" :selected_page="selected_item" :clickLinkNavbar="(index) => selected_item = index" />
  <WebView :pages="navigation" :select="selected_item" :creagePage="creagePage" />
</template>

  <script>
    import navbar from './components/navbar.vue';
    import WebView from './components/webView.vue'

    export default {
      components : {
        navbar, WebView
      },
      computed: {
        publishPage(){
          return this.navigation.filter(el => el.publish == true)
        }
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
            "title": pageObject.title,
            "url": pageObject.url,
            "content": pageObject.content,
            "current": false,
            "publish":pageObject.publish
          });

          console.log(this.navigation);
        }
    }
    }
    
  </script>

<style scoped>

</style>
