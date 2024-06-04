<template>
  <h1>Register</h1>
  <div>
    <v-sheet class="mx-auto" width="300">
      <v-form fast-fail @submit.prevent>
        <v-text-field
          v-model="username"
          :rules="usernameRules"
          label="Username"
        ></v-text-field>

        <v-text-field v-model="email" :rules="emailRules" label="Email"></v-text-field>

        <v-text-field
          v-model="password"
          :rules="[rules.required, rules.min]"
          label="Password"
        ></v-text-field>

        <v-text-field
          v-model="confirmPassword"
          :rules="[rules.required, passwordMatch]"
          label="Confirm Password"
        ></v-text-field>

        <v-btn class="mt-2" type="submit" @click="register" block>Register</v-btn>
      </v-form>
    </v-sheet>

    Already have an account?<v-btn variant="text" density="compact" @click="goToLogin"
      >Login</v-btn
    >
  </div>
</template>

<script>
import { auth, db } from "./Firebase.js";
import { createUserWithEmailAndPassword, updateProfile } from "firebase/auth";
import { collection, doc, setDoc } from "firebase/firestore";

export default {
  name: "LoginView",
  computed: {
    passwordMatch() {
      return () => this.password === this.confirmPassword || "Password must match";
    }
  },
  data: () => ({
    username: "",
    email: "",
    password: "",
    confirmPassword: "",
    usernameRules: [
      (value) => {
        // if (value?.length < 4 || value?.length > 16) return true;
        if (value?.length >= 4 && value?.length <= 16) return true;
        return "Username must be 4-16 characters.";
      },
    ],
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
    goToLogin() {
      this.$router.push("/login");
    },
    register() {
      const usersCollectionRef = collection(db, "Users");
      const username = this.username;
      const email = this.email;
      const password = this.password;
      createUserWithEmailAndPassword(auth, email, password)
        .then((userCredential) => {
          // Signed up
          const user = userCredential.user;
          console.log(user);
          // initialize user profile
          updateProfile(auth.currentUser, {
            displayName: username,
            photoURL:
              "https://cdn.vectorstock.com/i/preview-1x/15/32/colorful-profile-picture-placeholder-icon-vector-42411532.jpg",
          });
          // store user in Firestore db
          setDoc(doc(usersCollectionRef, auth.currentUser.uid), {
            bio: "",
            email: email,
            gender: "",
            username: username,
          });
        })
        .catch((error) => {
          const errorCode = error.code;
          const errorMessage = error.message;
          console.log(errorCode, errorMessage);
          // ..
        });
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
