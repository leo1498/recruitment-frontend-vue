<template>
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

<style lang="scss" scoped></style>