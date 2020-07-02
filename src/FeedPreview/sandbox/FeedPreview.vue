<template>
  <!-- Need to use single quotes inside for links: :url=" 'url' " or url="" -->
  <!-- Change the URL to see the error component. --> 
  <feed-preview :url="'https://www.gamespot.com/feeds/mashup/'"></feed-preview>
</template>

<script>
import ArticleList from "./../src/ArticleList";

export default {
  name: "FeedPreviewSandbox",
  components: {
    "feed-preview": ArticleList
  }
};
</script>