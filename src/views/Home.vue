<template>
  <div class="home">
  <v-btn @click="logout">Logout</v-btn>
  <h1>{{$store.getters.name}}</h1>
  <h1>User: {{$store.getters["user/name"]}}</h1>
  <h1>Token: {{$store.getters["user/token"]}}</h1>
  <!-- <h1> {{$store.getters["user/avatar"]}}</h1> -->
  <h1>Setting: {{$store.getters["settings/fixedHeader"]}}</h1>
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
