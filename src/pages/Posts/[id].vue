<template>
  <Layout>
    <div class="container">
      <div class="project-header">
        <h1 class="project-title">{{ post.title }}</h1>
        <div class="project-info">
          <div class="categories-container">
            <div class="categories">
              <span class="label">Categories</span>
              <span
                class="category"
                v-for="category in post.categories"
                :key="category.id"
                >{{ category.title }}</span
              >
            </div>
          </div>
          <div class="year-container">
            <span class="label">Year</span>
            <div>{{ time }}</div>
          </div>
        </div>
      </div>
      <div class="content">
        <div v-html="mdToHtml(post.content)"></div>
        <p>
          <img
            class="g-image g-image--lazy g-image--loaded"
            :src="GRIDSOME_API_URL + post.img.url"
            width="2560"
            data-sizes="(max-width: 2560px) 100vw, 2560px"
            sizes="(max-width: 2560px) 100vw, 2560px"
          />
        </p>
      </div>
    </div>
  </Layout>
</template>
<page-query>
    query {
        allStrapiPost {
            edges {
                node {
                id
                title
                subTitle
                content
                path
                created_at
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
    }
</page-query>
<script>
import moment from "moment"
import Markdown from "markdown-it"
const md = new Markdown()
export default {
  name: "Post",
  metaInfo() {
    return {
      title: this.post.title,
    }
  },
  computed: {
    post() {
      return this.$page.allStrapiPost.edges.find(
        (item) => item.node.id === this.$route.params.id
      )?.node
    },
    time() {
      return moment(this.post.created_at).format("YYYY")
    },
  },
  methods: {
    mdToHtml(content) {
      return md.render(content)
    },
  },
}
</script>
<style scoped>
.project-header {
  padding: 10vh 0 4rem;
}

.project-title {
  font-size: 4rem;
  margin: 0 0 4rem;
  padding: 0;
}

.project-info {
  display: flex;
  flex-wrap: wrap;
  font-size: 0.8rem;
}

.project-info > div {
  margin-right: 4rem;
}

.project-info > div:last-of-type {
  margin: 0;
}

.category:after {
  content: ", ";
}

.category:last-of-type:after {
  content: "";
}
</style>
