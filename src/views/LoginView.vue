<template>
  <v-form
    ref="form"
    class="ml-6 mr-6"
  >
    <v-text-field
      v-model="name"
      label="Name"
      required
    ></v-text-field>

    <v-text-field
      v-model="password"
      label="Password"
      type="password"
      required
    ></v-text-field>

    <v-btn
      color="success"
      class="mr-4"
      @click="login"
    >
      Login
    </v-btn>

    <v-btn
      color="error"
      class="mr-4"
      @click="$router.push({ name: 'register' })"
    >
      Register
    </v-btn>
  </v-form>
</template>

<script>
  import axios from "axios";
  export default {
    name: 'Login',
    data() {
      return {
        id: "",
        name: "",
        password: "",
      }
    },
    methods: {
      async login() {
        try { 
          var result = await axios.post("http://localhost:8080/api/login");
          window.localStorage.setItem("id", result.data.id);
          this.$router.push({ name: "home" });
        } catch (e) {
          alert("Credentiale incorecte!");
        }
      }
    }
  }
</script>