<template>
   <section class="container blog">
      <h2 class="blog__title">Blog</h2>

      <ArticleSearch />
      
      <div class="blog__wrapper">   
         <ArticleListItem 
         v-for="(article, index) of articles.items"
         :article="article"
         :key="index"
         />
      </div>
   </section>
</template>

<script>
import ArticleListItem from './ArticleListItem';
import ArticleSearch from './ArticleSearch';

export default {
   name: "FeedPreviewListTpl",
   components: {
      ArticleListItem, ArticleSearch
   },
   props: ["url"],
   data() {
      return {
         articles: [],
      }
   },
   mounted() {
      // vue-rss-parser is an alternative way. But I used API rss2json
      fetch(`https://api.rss2json.com/v1/api.json?rss_url=${this.url}%2Frss`)
         .then(response => response.json())
         .then(json => this.articles = json);    
   }
};
</script>

<style lang="scss" scoped>
.blog{

   &__title{
      margin: 20px 0;
      text-align: center;
      font-size: 6rem;
      font-weight: 700;
      line-height: 1.3;
      position: relative;

       &::before{
         content: '';
         position: absolute;
         top: 50%;
         left: 50%;
         transform: translate(-50%, -50%);
         width: 100px;
         height: 100px;
         border-radius: 50%;
         background-color: #5D86DE;
         z-index: -1;
         animation: .5s circle ease-in-out;
      }
   }

   &__wrapper{
      display: flex;
      justify-content: center;
      align-items: flex-start;
      flex-wrap: wrap;
      margin: 40px 0;
      position: relative;
      animation: .5s appear;

      &::before{
         content: 'Search';
         position: absolute;
         top: 0;
         left: 50%;
         transform: translateX(-50%);
         font-size: 20rem;
         color: rgba(0,0,0,.02);
         line-height: 0;
         font-weight: 900;
         letter-spacing: 5px;
         letter-spacing: 5px;
         z-index: -1;
      }
   }

   @keyframes circle{
      0% {
         transform: translate(-50%, -50%) scale(0);
         transform-origin: center;
      }
      100% {
         transform: translate(-50%, -50%) scale(1);
      }
   }

   @keyframes appear{
      0% {
         opacity: 0;
         transform: translateY(30px);
      }
      100% {
         opacity: 1;
         transform: translateY(0);
      }
   }
}
</style>
