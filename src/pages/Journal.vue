<template>
  <Layout>
    <div class="container">
      <div class="journal-hero">
        <h1 class="journal-header">
          a wise person once said...
        </h1>
      </div>
    </div>
    <g-link
      :to="`/journal/${node.id}`"
      class="journal-post"
      v-for="{ node } in journals"
      :key="node.id"
      ><div class="container journal">
        <h2 class="journal-title">
          {{ node.title }}
        </h2>
        <p class="journal-excerpt">
          {{ node.subTitle }}
        </p>
      </div></g-link
    >
  </Layout>
</template>
<page-query>
  query {
    allStrapiLatest(sortBy:"id", order: ASC) {
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
export default {
  metaInfo: {
    title: "Journal",
  },
  computed: {
    journals() {
      return this.$page.allStrapiLatest.edges
    },
  },
}
</script>
<style scoped>
.journal-hero {
  padding: 4rem 0;
  text-align: center;
  color: var(--color-base-1);
}

.journal-header {
  font-size: 3rem;
  font-weight: 700;
  padding: 0;
  margin: 0;
}

.journal-post {
  display: block;
  padding: 2rem 0;
  text-decoration: none;
  transition: 0.5s ease;
}

.journal-post > div {
  transition: transform 0.5s ease;
}

.journal-post:hover {
  background-color: var(--color-base-1);
}

.journal-post:hover > .journal {
  transform: translateX(4rem);
}

.journal-post h1,
.journal-post h2 {
  margin: 0;
  padding: 0;
}

.journal-title {
  font-size: 2rem;
  color: var(--color-contrast);
}

.journal-excerpt {
  color: var(--color-contrast-1);
}

@media (min-width: 560px) {
  .journal-post {
    padding: 3rem 0;
  }
}

@media (min-width: 860px) {
  .journal-post {
    padding: 5rem 0;
  }
}
</style>
