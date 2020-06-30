<template>
  <section>
    <h2>Lists</h2>
    <div>   
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

export default {
  name: "FeedPreviewListTpl",
  components: {
    ArticleListItem
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
  h2{
    color: pink;
  }
</style>
