<template>
   <article class="blog-item">
      <a :href="article.link" target="_blank" class="blog-item__picture">
         <img :src="article.enclosure.link" :alt="article.title" />
      </a>
      <div class="blog-item__content">
         <a :href="article.link" target="_blank" class="blog-item__title">{{ article.title }}</a>
         <time :datetime="article.pubDate" class="blog-item__date">{{ article.pubDate | date }}</time>
      </div>
   </article>      
</template>

<script>
import moment from 'moment';

export default {
   name: "ArticleListItemTpl",
   props: {
      article: {
         type: Object,
         required: true
      }
   },
   filters: {
      date: function(date) {
         return moment(date).format('MMMM Do YYYY, h:mm a');
      }
   }
};
</script>

<style lang="scss" scoped>
@import "@/assets/variables.scss";

.blog-item{
   width: 100%;
   max-width: 480px;
   margin: 15px 0;
   background-color: #fff;
   box-shadow: 0 7px 20px 4px rgba(0,0,0,.07);
   border-radius: 7px;
   overflow: hidden;
   animation: .5s appear;

   @media #{$mobile} {
      width: 50%;
      margin: 20px;
   }

   &:hover{
      .blog-item__picture{
         img{
            opacity: .9;
            transform: scale(1.05);
         }
      }
   }

   &__picture{
      display: block;
      margin-bottom: 20px;
      border-bottom: 5px solid map-get($map: $colors, $key: primary);
      overflow: hidden;
      will-change: transform;

      img{
         display: block;
         max-width: 100%;
         transition: opacity .3s ease-in-out, transform .3s ease-in-out;
      }
   }

   &__content{
      padding: 5px 30px 20px;
   }

   &__title{
      display: block;
      margin-bottom: 20px;
      font-size: 1.6rem;
      line-height: 1.5;
      font-weight: 700;
   }

   &__date{
      display: block;
      width: 100%;
      padding-top: 15px;
      border-top: 1px solid #eee;
      font-size: 1.2rem;
      color: #777;
   }
}
</style>
