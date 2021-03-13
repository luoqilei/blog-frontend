<template>
  <Layout>
    <div class="journal">
      <div class="container journal-container">
        <div class="journal-header">
          <h1 class="journal-title">
            {{ journal.title }}
          </h1>
          <div class="journal-meta">
            <div class="journal-author">
              <span class="label">Author</span
              ><span class="author-name">{{ journal.author }}</span>
            </div>
            <div class="journal-date">
              <span class="label">Date</span>
              <div data-v-2a0eef53="">{{ time }}</div>
            </div>
            <div class="journal-time">
              <span class="label">Time</span
              ><span data-v-2a0eef53="">{{ journal.time }}</span>
            </div>
          </div>
        </div>
        <div class="journal-content">
          <div v-html="mdToHtml(journal.content)"></div>
          <p v-if="journal.img">
            <img
              class="g-image g-image--lazy g-image--loading"
              :src="GRIDSOME_API_URL + journal.img.url"
              width="2560"
              data-sizes="(max-width: 2560px) 100vw, 2560px"
              sizes="(max-width: 2560px) 100vw, 2560px"
            />
          </p>
        </div>
      </div>
    </div>
  </Layout>
</template>
<page-query>
  query {
    allStrapiLatest {
      edges {
        node {
          id
          title
          subTitle
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
import moment from "moment"
import Markdown from "markdown-it"
const md = new Markdown()
export default {
  name: "JournalInfo",
  metaInfo() {
    return {
      title: this.journal.title,
    }
  },
  computed: {
    journal() {
      return (
        this.$page.allStrapiLatest.edges.find(
          (item) => item.node.id === this.$route.params.id
        )?.node || {
          id: "1",
          title: "2",
          subTitle: "3",
          content: "4",
          created_at: 1423213123123,
          author: "",
          time: "",
          img: {
            url: "1.png",
          },
        }
      )
    },
    time() {
      return moment(this.journal.created_at).format("DD.MMM YYYY")
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
.journal-container {
  max-width: 840px;
}

.journal-header {
  padding: 2rem 0 4rem;
}

.journal-title {
  font-size: 4rem;
  margin: 0 0 4rem;
  padding: 0;
}

.journal-meta {
  display: flex;
  flex-wrap: wrap;
  font-size: 0.8rem;
}

.journal-meta > div {
  margin-right: 4rem;
}

.journal-meta > div:last-of-type {
  margin: 0;
}
</style>
