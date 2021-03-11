<template>
  <Layout>
    <div class="container">
      <div class="hero">
        <h1 class="hero-title">Simplicity. Aesthetics. Value.</h1>
        <h2 class="hero-subtitle">
          Hi there, I'm an independent Digital Designer &amp; Art Director
          focused on digital design for brands that like to have fun.
        </h2>
      </div>
      <div class="projects">
        <div class="project" v-for="{ node } in posts" :key="node.id">
          <g-link href="/projects/chelsea-landmark/" class="project-link">
            <img
              :src="`http://localhost:1337${node.img.url}`"
              alt=""
              class="thumbnail g-image g-image--lazy g-image--loaded"
            />
            <h3 class="project-title">{{ node.title }}</h3>
            <div class="categories">
              <span
                class="category"
                v-for="category in node.categories"
                :key="category.id"
                >{{ category.title }}</span
              >
            </div>
          </g-link>
        </div>
      </div>
    </div>
    <Latest />
  </Layout>
</template>
<page-query>
  query {
    allStrapiPost(sortBy:"id", order: ASC) {
      edges {
        node {
          id
          title
          subTitle
          content
          path
          categories {
            id
            title
          }
          img {
            url
          }
        }
      }
    }
    allStrapiLatest(sortBy:"id", order: ASC) {
      edges {
        node {
          id
          title
          content
          author
          created_at
          time
          img {
            url
          }
        }
      }
    }
  }
</page-query>
<script>
import Latest from "../components/Latest"
export default {
  metaInfo: {
    title: "Hello, world!",
  },
  components: { Latest },
  computed: {
    posts() {
      return this.$page.allStrapiPost.edges
    },
    latests() {
      return this.$page.allStrapiLatest.edges
    },
  },
}
</script>

<style></style>
