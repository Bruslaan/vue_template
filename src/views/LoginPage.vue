<template>
  <v-app>
    <v-content>
      <v-container class="mt-12" fluid>
        <v-row align="center" justify="center">
          <v-col cols="12" sm="8" md="4">
            <v-card outlined>
              <v-card-text>
                <v-form>
                  <h1 class="my-5">Vanilla</h1>
                  <v-text-field v-model="email" label="Login" name="login" type="text" />

                  <v-text-field
                    v-model="password"
                    id="password"
                    label="Password"
                    name="password"
                    type="password"
                  />
                  <p v-if="errorMessage">{{errorMessage}}</p>
                </v-form>
              </v-card-text>
              <v-card-actions>
                <v-spacer />
                <v-btn outlined :loading="loading" :disabled="loading" @click="loginUser">Login</v-btn>
              </v-card-actions>
            </v-card>
          </v-col>
        </v-row>
      </v-container>
    </v-content>
  </v-app>
</template>

<script>
export default {
  data() {
    return {
      email: "",
      password: "",
      errorMessage: "",
      loading: false
    };
  },
  methods: {
    loginUser() {
      this.loading = true;
      let self = this
      self.$store
        .dispatch("loginUser", { email: this.email, password: this.password })
        .then(user => {
          self.$store.dispatch("setUser", user);
          self.$router.replace("home");
          self.loading = false;
        })
        .catch(function(error) {
          window.console.log("Error getting documents: ", error);
          self.errorMessage = error
           self.loading = false;
        });

     
    }
  }
};
</script>