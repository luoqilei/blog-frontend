<template>
  <Layout>
    <div class="container">
      <div class="contact-header">
        <h1 class="contact-title">Say hi!</h1>
        <p>
          Leave me a note with any questions you might have, I'll get back to
          you as soon as possible.
        </p>
      </div>
      <form name="contact" class="contact-form">
        <div class="sender-info">
          <div>
            <label for="name" class="label">Your name</label
            ><input
              type="text"
              name="name"
              v-model="contactInfo.name"
              required
            />
          </div>
          <div>
            <label for="email" class="label">Your email</label
            ><input
              type="email"
              name="email"
              v-model="contactInfo.email"
              email
            />
          </div>
        </div>
        <div class="message">
          <label for="message" class="label">Message</label
          ><textarea name="message" v-model="contactInfo.message"></textarea>
        </div>
        <button class="button" @click.prevent="contact">Submit form</button>
      </form>
    </div>
  </Layout>
</template>

<script>
import axios from "axios"
export default {
  name: "Contact",
  metaInfo: {
    title: "Contact",
  },
  data() {
    return {
      contactInfo: {
        name: "",
        email: "",
        message: "",
      },
    }
  },
  methods: {
    async contact() {
      try {
        await axios({
          method: "POST",
          url: `${this.GRIDSOME_API_URL}/contacts`,
          data: this.contactInfo,
        })
        this.$router.push("/")
      } catch (error) {
        alert("请检查信息")
      }
    },
  },
}
</script>

<style></style>
