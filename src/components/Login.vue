<template>
  <h1>Login</h1>
  <div>
    <v-sheet class="mx-auto" width="300">
      <v-form @submit.prevent>
        <v-text-field v-model="email" :rules="emailRules" label="Email"></v-text-field>
        <v-text-field
          v-model="password"
          :rules="[rules.required, rules.min]"
          label="Password"
        ></v-text-field>

        <v-btn class="mt-2" type="submit" v-on:click="login" block>Login</v-btn>
        <v-btn class="mt-2" type="submit" v-on:click="loginWithGoogle" block
          >Login with Google</v-btn
        >
      </v-form>
    </v-sheet>
    Don't have an account?<v-btn variant="text" density="compact" @click="goToRegister"
      >Register</v-btn>
  </div>
</template>

<script>
import { auth } from "./Firebase.js";
import {
  signInWithEmailAndPassword,
  signInWithPopup,
  GoogleAuthProvider,
  setPersistence,
  browserLocalPersistence,
} from "firebase/auth";

export default {
  name: "LoginView",
  data: () => ({
    email: "",
    password: "",
    emailRules: [
      (v) => !!v || "Required",
      (v) => /.+@.+\..+/.test(v) || "E-mail must be valid",
    ],
    rules: {
      required: (value) => !!value || "Required.",
      min: (v) => (v && v.length >= 8) || "Min 8 characters",
    },
  }),
  methods: {
    goToRegister() {
      this.$router.push("/register");
    },
    login() {
      const email = this.email;
      const password = this.password;
      signInWithEmailAndPassword(auth, email, password);
      setPersistence(auth, browserLocalPersistence)
        .then(() => {
          this.$router.push("/");
        })
        .catch((error) => {
          console.error(error);
        });
    },
    loginWithGoogle() {
      const googleProvider = new GoogleAuthProvider();
      signInWithPopup(auth, googleProvider);
    },
  },
};
</script>

<style>
form {
  display: flex;
  flex-direction: column;
  justify-content: center;
  margin: 25px;
}
</style>
