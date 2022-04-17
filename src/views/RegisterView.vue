<template>
  <v-form ref="form" class="ml-6 mr-6">
    <v-text-field v-model="name" label="User Name" required></v-text-field>

    <v-text-field
      v-model="password"
      label="Password"
      type="password"
      required
    ></v-text-field>

    <v-btn color="success" class="mr-4" @click="register"> Register </v-btn>
  </v-form>
</template>

<script>
import axios from "axios";
export default {
  name: "Login",
  data() {
    return {
      name: "",
      password: "",
    };
  },
  methods: {
    async register() {  
      try {  
        var result = await axios.post("http://localhost:8080/api/users", {
          user_name: this.name,
          user_password: this.password,
          user_isAdmin: false,
        });
        this.$router.push({ name: "AdminPanel" });
      } catch (e) {}
    },
  },
};
</script>