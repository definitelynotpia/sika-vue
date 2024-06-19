<template>
  <div>
    <v-container>
      <v-row align="center" justify="center" style="height: 90vh;" no-gutters>
        <v-stepper :items="['Create your Avatar', 'Register your account', 'Begin your journey']"
          bg-color="teal-lighten-5" min-width="1500">

          <template v-slot:[`item.1`]>
            <v-row align="center" justify="space-around" no-gutters>
              <v-col cols="4">
                <v-avatar ref="avatar" :image="displayAvatar" rounded="0" size="100%"></v-avatar>
              </v-col>

              <v-col cols="7">
                <v-card color="light-green-lighten-4" width="100%">

                  <v-tabs v-model="tab" align-tabs="center" variant="text" bg-color="yellow-darken-3">
                    <v-tab value="skinColor">skinColor</v-tab>
                    <v-tab value="eyes">eyes</v-tab>
                    <v-tab value="mouth">mouth</v-tab>
                    <v-tab value="hair">hair</v-tab>
                    <v-tab value="hairColor">hairColor</v-tab>
                    <v-tab value="accessories">accessories</v-tab>
                    <v-tab value="bgColor">bgColor</v-tab>
                  </v-tabs>

                  <v-card-text>
                    <v-tabs-window v-model="tab">
                      <v-tabs-window-item value="skinColor">
                        <v-btn-toggle v-model="skinColor" variant="outlined" class="flex-wrap" mandatory>
                          <v-btn value="8c5a2b" style="background: #8c5a2b;" rounded="xl" size="x-large" class="mx-3 border-lg"></v-btn>
                          <v-btn value="a47539" style="background: #a47539;" rounded="xl" size="x-large" class="mx-3 border-lg"></v-btn>
                          <v-btn value="c99c62" style="background: #c99c62;" rounded="xl" size="x-large" class="mx-3 border-lg"></v-btn>
                          <v-btn value="e2ba87" style="background: #e2ba87;" rounded="xl" size="x-large" class="mx-3 border-lg"></v-btn>
                          <v-btn value="efcc9f" style="background: #efcc9f;" rounded="xl" size="x-large" class="mx-3 border-lg"></v-btn>
                          <v-btn value="f5d7b1" style="background: #f5d7b1;" rounded="xl" size="x-large" class="mx-3 border-lg"></v-btn>
                          <v-btn value="ffe4c0" style="background: #ffe4c0;" rounded="xl" size="x-large" class="mx-3 border-lg"></v-btn>
                        </v-btn-toggle>
                      </v-tabs-window-item>

                      <v-tabs-window-item value="eyes">
                        <v-btn-toggle v-model="eyes" variant="text" class="flex-wrap" mandatory>
                          <v-btn value="cheery" rounded="xl" size="x-large" class="mx-1 border-lg">cheery</v-btn>
                          <v-btn value="starstruck" rounded="xl" size="x-large" class="mx-1 border-lg">starstruck</v-btn>
                          <v-btn value="winking" rounded="xl" size="x-large" class="mx-1 border-lg">winking</v-btn>
                          <v-btn value="normal" rounded="xl" size="x-large" class="mx-1 border-lg">normal</v-btn>
                        </v-btn-toggle>
                      </v-tabs-window-item>

                      <v-tabs-window-item value="mouth">
                        <v-btn-toggle v-model="mouth" variant="text" class="flex-wrap" mandatory>
                          <v-btn value="braces" rounded="xl" size="x-large" class="mx-1 border-lg">braces</v-btn>
                          <v-btn value="gapSmile" rounded="xl" size="x-large" class="mx-1 border-lg">gapSmile</v-btn>
                          <v-btn value="kawaii" rounded="xl" size="x-large" class="mx-1 border-lg">kawaii</v-btn>
                          <v-btn value="openedSmile" rounded="xl" size="x-large" class="mx-1 border-lg">openedSmile</v-btn>
                          <v-btn value="teethSmile" rounded="xl" size="x-large" class="mx-1 border-lg">teethSmile</v-btn>
                          <v-btn value="awkwardSmile" rounded="xl" size="x-large" class="mx-1 border-lg">awkwardSmile</v-btn>
                        </v-btn-toggle>
                      </v-tabs-window-item>

                      <v-tabs-window-item value="hair">
                        <v-btn-toggle v-model="hair" variant="text" class="flex-wrap" mandatory>
                          <v-btn value="curlyBob" rounded="xl" size="x-large" class="mx-1 border-lg">curlyBob</v-btn>
                          <v-btn value="straightHair" rounded="xl" size="x-large" class="mx-1 border-lg">straightHair</v-btn>
                          <v-btn value="shortHair" rounded="xl" size="x-large" class="mx-1 border-lg">shortHair</v-btn>
                          <v-btn value="shavedHead" rounded="xl" size="x-large" class="mx-1 border-lg">shavedHead</v-btn>
                          <v-btn value="mohawk" rounded="xl" size="x-large" class="mx-1 border-lg">mohawk</v-btn>
                          <v-btn value="halfShavedHead" rounded="xl" size="x-large" class="mx-1 border-lg">halfShavedHead</v-btn>
                          <v-btn value="froBun" rounded="xl" size="x-large" class="mx-1 border-lg">froBun</v-btn>
                          <v-btn value="curlyShortHair" rounded="xl" size="x-large" class="mx-1 border-lg">curlyShortHair</v-btn>
                        </v-btn-toggle>
                      </v-tabs-window-item>

                      <v-tabs-window-item value="hairColor">
                        <v-btn-toggle v-model="hairColor" variant="outlined" class="flex-wrap" mandatory>
                          <v-btn value="220f00" style="background: #220f00" rounded="xl" size="x-large" class="mx-1 border-lg"></v-btn>
                          <v-btn value="238d80" style="background: #238d80" rounded="xl" size="x-large" class="mx-1 border-lg"></v-btn>
                          <v-btn value="3a1a00" style="background: #3a1a00" rounded="xl" size="x-large" class="mx-1 border-lg"></v-btn>
                          <v-btn value="605de4" style="background: #605de4" rounded="xl" size="x-large" class="mx-1 border-lg"></v-btn>
                          <v-btn value="71472d" style="background: #71472d" rounded="xl" size="x-large" class="mx-1 border-lg"></v-btn>
                          <v-btn value="d56c0c" style="background: #d56c0c" rounded="xl" size="x-large" class="mx-1 border-lg"></v-btn>
                          <v-btn value="e2ba87" style="background: #e2ba87" rounded="xl" size="x-large" class="mx-1 border-lg"></v-btn>
                          <v-btn value="e9b729" style="background: #e9b729" rounded="xl" size="x-large" class="mx-1 border-lg"></v-btn>
                        </v-btn-toggle>
                      </v-tabs-window-item>

                      <v-tabs-window-item value="accessories">
                        <v-btn-toggle v-model="accessories" variant="text" class="flex-wrap" mandatory>
                          <v-btn value="">none</v-btn>
                          <v-btn value="glasses">glasses</v-btn>
                          <v-btn value="catEars">catEars</v-btn>
                          <v-btn value="clownNose">clownNose</v-btn>
                          <v-btn value="faceMask">faceMask</v-btn>
                          <v-btn value="sailormoonCrown">sailormoonCrown</v-btn>
                          <v-btn value="sunglasses">sunglasses</v-btn>
                          <v-btn value="sleepMask">sleepMask</v-btn>
                          <v-btn value="mustache">mustache</v-btn>
                        </v-btn-toggle>
                      </v-tabs-window-item>

                      <v-tabs-window-item value="bgColor">
                        <v-btn-toggle v-model="bgColor" variant="outlined" class="flex-wrap" mandatory>
                          <v-btn value="b6e3f4" style="background: #b6e3f4" rounded="xl" size="x-large" class="mx-3 border-lg"></v-btn>
                          <v-btn value="c0aede" style="background: #c0aede" rounded="xl" size="x-large" class="mx-3 border-lg"></v-btn>
                          <v-btn value="d1d4f9" style="background: #d1d4f9" rounded="xl" size="x-large" class="mx-3 border-lg"></v-btn>
                          <v-btn value="ffd5dc" style="background: #ffd5dc" rounded="xl" size="x-large" class="mx-3 border-lg"></v-btn>
                          <v-btn value="ffdfbf" style="background: #ffdfbf" rounded="xl" size="x-large" class="mx-3 border-lg"></v-btn>
                        </v-btn-toggle>
                      </v-tabs-window-item>
                    </v-tabs-window>
                  </v-card-text>

                </v-card>
              </v-col>
            </v-row>
          </template>

          <template v-slot:[`item.2`]>
            <v-card flat>
              <v-form @submit.prevent>
                <v-text-field v-model="username" :rules="usernameRules" label="Username"></v-text-field>
                <v-btn class="mt-2" type="submit" v-on:click="login" block>Login</v-btn>
              </v-form>
              <v-btn class="mt-2" color="blue-darken-3" type="submit" v-on:click="loginWithGoogle" block>
                Login with Google
              </v-btn>
            </v-card>
          </template>

          <template v-slot:[`item.3`]>
            <v-card title="Step Three" flat>...</v-card>
          </template>
        </v-stepper>
      </v-row>
    </v-container>
  </div>
</template>

<script>
// firebase
import { auth } from "./Firebase.js";
import {
  signInWithEmailAndPassword,
  signInWithPopup,
  GoogleAuthProvider,
  setPersistence,
  browserLocalPersistence,
} from "firebase/auth";
// avatar API
import { createAvatar } from '@dicebear/core';
import { bigSmile } from '@dicebear/collection';
// icons
// import SvgIcon from '@jamescoyle/vue-icon';
// import { mdiRefresh } from '@mdi/js';

export default {
  name: "LoginView",
  // components: {
  //   SvgIcon
  // },
  data: () => ({
    // avatar
    skinColor: "e2ba87",
    eyes: "cheery",
    mouth: "braces",
    hair: "curlyBob",
    hairColor: "605de4",
    accessories: "glasses",
    bgColor: "c0aede",
    // icon
    // mdiRefresh: mdiRefresh,
    // auth
    tab: null,
    username: "",
    usernameRules: [
      (v) => !!v || "Required",
      (v) => /^(?=.{8,20}$)(?![.-])(?!.*[.]{2})[a-zA-Z0-9.-]+(?<![.])$/.test(v) || "Username must be 8-20 characters long. Avoid adding underscores, dashes, and periods.",
    ],
  }),
  computed: {
    setAccessories() {
      if (this.accessories == "") {
        return 0;
      } else {
        return 100;
      }
    },
    displayAvatar() {
      const avatar = createAvatar(bigSmile, {
        "skinColor": [this.skinColor],
        "eyes": [this.eyes],
        "mouth": [this.mouth],
        "hair": [this.hair],
        "hairColor": [this.hairColor],
        "accessories": [this.accessories],
        "accessoriesProbability": this.accessories == "" ? 0 : 100,
        "backgroundColor": [this.bgColor],
      }).toDataUri();
      return avatar;
    }
  },
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
body {
  background: thistle;
}

form {
  display: flex;
  flex-direction: column;
  justify-content: center;
  margin: 25px;
}
</style>
