<template>
  <article>
    <pre>
    {{ article.title }}
    </pre>
    <img :src="article.enclosure.link" :alt="article.title" />
     <div v-html="article.description"> </div>
     <div>{{ article.pubDate }}</div>
     <hr />
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
</style>
