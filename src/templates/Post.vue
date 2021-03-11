<template>
  <div>
    123
  </div>
</template>
<page-query>
    query($id: ID!) {
        strapiPost (id: $id) {
            id
            title,
            content,
            subTitle
        }
    }
</page-query>
<script>
export default {
  name: "Post",
}
</script>

<style></style>
