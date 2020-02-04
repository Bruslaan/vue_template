<template>
  <v-navigation-drawer v-model="drawer" mobile-break-point="900" left app>
    <template v-slot:prepend>
      <v-list-item two-line>
        <v-list-item-avatar>
          <img src="https://randomuser.me/api/portraits/women/81.jpg" />
        </v-list-item-avatar>

        <v-list-item-content>
          <v-list-item-title>{{$store.getters["user/name"]}}</v-list-item-title>
          <v-list-item-subtitle>Status oder So</v-list-item-subtitle>
        </v-list-item-content>
      </v-list-item>
    </template>

    <v-divider></v-divider>

    <v-list dense>
      <v-list-item v-for="item in items" :key="item.title" :to="item.to">
        <v-list-item-icon>
          <v-icon>{{ item.icon }}</v-icon>
        </v-list-item-icon>
        <v-list-item-content>
          <v-list-item-title>{{ item.title }}</v-list-item-title>
        </v-list-item-content>
      </v-list-item>
    </v-list>
  </v-navigation-drawer>
</template>
<script>
export default {
  props: {
    value: Boolean
  },
  watch: {
    value: function() {
      this.drawer = this.value;
    },
    drawer: function() {
      this.$emit("input", this.drawer);
    }
  },
  data() {
    return {
      drawer: true,
      items: [
        { title: "Home", icon: "mdi-home-city", to: "test" },
        { title: "My Account", icon: "mdi-account", to: "dashboard" },
        { title: "Users", icon: "mdi-account-group-outline" }
      ]
    };
  }
};
</script>