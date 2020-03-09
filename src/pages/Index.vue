<template>
  <Layout>
    <div class="container">
      <h1 class="text-4xl text-pink-500">List articles</h1>
      <div v-for="article in $page.articles.edges" :key="article.id" class="article d-flex">
        <div>
          <div
            class="article__img"
            :style="{ 'background-image': 'url(' + article.node.image + ')' }"
          ></div>
        </div>
        <div class="article__body">
          <g-link :to="article.node.path" class="article__link"></g-link>
          <h1 class="article__title">{{article.node.title}}</h1>
          <p class="article__abstract">{{article.node.abstract}}</p>
        </div>
      </div>
    </div>
  </Layout>
</template>
<page-query>
query {
  articles: allArticles {
    edges {
      node {
        title
        excerpt
        image
        path
      }
    }
  }
}
</page-query>
<script>
export default {
  metaInfo: {
    title: "Le Kino"
  }
};
</script>

<style>
</style>
