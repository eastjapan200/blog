<template>
  <main class="main">
    <h1 class="title">{{title}}</h1>
    <p class="publishedAt">{{publishedAt}}</p>
    <div class="post" v-html="body"></div>
  </main>
</template>

<script>
import axios from 'axios'

export default {
  async asyncData({ params }) {

    console.log(params);

    const { data } = await axios.get(
      `https://t1964101.microcms.io/api/v1/blog/${params.slug}`,
      {
        headers: { 'X-API-KEY': '36847a75-600f-438f-b270-1a08a33fc637' }
      }
    );
    

    return data
  }
}
</script>

<style lang="scss" scoped>
.main {
  width:960px;
  margin:0 auto;
}

.title {
  margin-bottom: 20px;
}

.publishedAt {
  margin-bottom:40px;
}

.post {
  & >h1 {
    font-size: 30px;
    font-weight: bold;
    margin: 40px 0 20px;
    background-color: #eee;
    padding: 10px 20px;
    border-radius: 5px;
  }

  & > h2 {
    font-size: 24px;
    font-weight: bold;
    margin: 40px 0 16px;
    border-bottom: 1px solid #ddd;
  }

  & > p {
    line-height: 1.8;
    letter-spacing: 0.2px
  }
  
  & > ol {
    list-style-type:decimal;
    list-style-position:inside;
  }
}
</style>