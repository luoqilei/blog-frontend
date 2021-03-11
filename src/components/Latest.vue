<template>
  <div>
    <div class="latest-journals-heading container">
      <span class="label">Latest and greatest</span>
    </div>
    <div class="latest-journals">
      <div class="container">
        <a
          href="/journal/gridsome-forestry-cms/"
          class="journal"
          v-for="{ node } in latests"
          :key="node.id"
        >
          <h3 class="journal-title">
            {{ node.title }}
          </h3>
        </a>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "Latest",
  computed: {
    latests() {
      return this.$page.allStrapiLatest.edges
    },
  },
}
</script>

<style></style>
