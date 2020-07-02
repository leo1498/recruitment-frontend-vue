<template>
<div class="blog">
   <section class="container">
      <h2 class="blog__title">Blog</h2>

      <!-- Search -->
      <ArticleSearch v-model="search" v-on:input="search = $event" />

      <!-- Loader -->
      <Loader v-if="loading" />

      <!-- If something is wrong -->
      <div v-else-if="dataStatusError">
         <FetchDataError :dataErrMsg="dataErrorMsg" />
      </div>

      <div v-else>

         <!-- Blog news items -->
         <div v-if="filterArticles.length" class="blog__wrapper">   
            <ArticleListItem 
               v-for="(article, index) in filterArticles"
               :article="article"
               :key="index"
            />
         </div>

         <!-- If not found -->
         <p v-else class="blog__not-found">No news found :(</p>
      </div>
   </section>
</div>
</template>

<script>
import ArticleListItem from "./ArticleListItem";
import ArticleSearch from "./ArticleSearch";
import FetchDataError from "./FetchDataError";
import Loader from "@/Loader";

export default {
   name: "FeedPreviewListTpl",
   components: {
      ArticleListItem,
      ArticleSearch,
      FetchDataError,
      Loader,
   },
   props: ["url"], // get rss URL
   data() {
      return {
         articles: [], // array for news
         search: "", // string for filter search
         dataStatusError: false, // error checking data receiving
         dataErrorMsg: '', // fetch data error message
         loading: true, // loader
      }
   },
   async mounted() {
      // vue-rss-parser is an alternative way. But I used API rss2json
      await fetch(`https://api.rss2json.com/v1/api.json?rss_url=${this.url}%2Frss`)
         .then(res => {
            if (res.status == 200) {
               return res.json();
            } else {
               this.dataStatusError = true; // enable error component
               throw new Error(`${res.status} | ${res.url}`);
            }
         })
         .then(json => this.articles = json.items)
         .catch(error => this.dataErrorMsg = error); // error message text
         this.loading = false; // disable loader
   },
   computed: {
      // news search method
      filterArticles() {
         return this.articles.filter(article => 
            article.title.toLowerCase().includes(this.search.toLowerCase())
         );
      }
   }
};
</script>

<style lang="scss" scoped>
@import "@/assets/variables.scss";

.blog{
   overflow-x: hidden;

   &__title{
      margin: 20px 0;
      text-align: center;
      font-size: 6rem;
      font-weight: 700;
      line-height: 1.3;
      position: relative;

      &::before{
         content: "";
         position: absolute;
         top: 50%;
         left: 50%;
         transform: translate(-50%, -50%);
         width: 100px;
         height: 100px;
         border-radius: 50%;
         background-color: map-get($map: $colors, $key: primary);
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
   }

   &__not-found{
      text-align: center;
      font-size: 2rem;
      color: #999;
      animation: .5s appear;

      @media #{$mobile} {
         padding-top: 30px;
      }
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
</style>
