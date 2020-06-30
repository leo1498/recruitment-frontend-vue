<template>
   <article class="blog-item">
      <div class="blog-item__picture">
         <img :src="article.enclosure.link" :alt="article.title" />
      </div>
      <div class="blog-item__content">
         <h3 class="blog-item__title">{{ article.title }}</h3>
         <!-- <div v-html="article.description" class="blog-item__desc"></div> -->
         <time :datetime="article.pubDate" class="blog-item__date">{{article.pubDate}}</time>
      </div>
   </article>      
</template>

<script>
export default {
   name: "FeedPreviewListTpl",
   props: {
      article: {
         type: Object,
         required: true
      }
   }
};
</script>

<style lang="scss" scoped>
.blog-item{
   width: 50%;
   max-width: 480px;
   margin: 20px;
   background-color: #fff;
   box-shadow: 0 7px 20px 4px rgba(0,0,0,.07);
   border-radius: 7px;
   overflow: hidden;

   &:hover{
      .blog-item__picture{
         img{
            opacity: .9;
            transform: scale(1.05);
         }
      }
   }

   &__picture{
      margin-bottom: 20px;
      border-bottom: 5px solid #5D86DE;
      overflow: hidden;
      will-change: transform;
      img{
         max-width: 100%;
         transition: opacity .3s ease-in-out, transform .3s ease-in-out;
      }
   }

   &__content{
      padding: 5px 30px 20px;
   }

   &__title{
      margin-bottom: 20px;
      font-size: 1.6rem;
      line-height: 1.5;
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
