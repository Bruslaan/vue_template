<template>
  <div class="home">
  
    <h1>Hallo</h1>
  <v-btn @click="logout">Logout</v-btn>
  </div>
</template>

<script>
// @ is an alias to /src

export default {
  name: "home",
    methods: {

    async logout() {
      await this.$store.dispatch('user/logout')
      this.$router.push(`/login?redirect=${this.$route.fullPath}`)
    }
  },
  components: {}
};
</script>
