<template>
  <div>
    <v-container>
      <v-row align="center" justify="center" style="height: 90vh;" no-gutters>
        <v-stepper :items="['Create your Avatar', 'Register your account', 'Begin your journey']"
          bg-color="teal-lighten-5" min-width="1500">

          <template v-slot:[`item.1`]>
            <v-row align="center" justify="space-around" no-gutters>
              <v-col cols="3">
                <v-avatar ref="avatar" :image="displayAvatar" size="100%"></v-avatar>
                <v-text-field v-model="username" :rules="[required, usernameRules]" label="Username" variant="solo"
                  class="mt-5"></v-text-field>
                <v-row>
                  <v-col>
                    <v-date-input v-model="date" label="Date of Birth" prepend-icon="" variant="solo" required></v-date-input>
                  </v-col>
                  <v-col>
                    <v-text-field v-model="pronouns" :rules="[required]" label="Pronouns" variant="solo"></v-text-field>
                  </v-col>
                </v-row>

              </v-col>

              <v-col cols="8">
                <v-card color="light-green-lighten-4" height="500" width="950">

                  <v-tabs v-model="tab" align-tabs="center" variant="text" bg-color="yellow-darken-3" height="60">
                    <v-tab value="skinColor">
                      <v-img width="50" max-width="50" :src="require('../assets/skin.svg')"/>
                    </v-tab>
                    <v-tab value="eyes">
                      <v-img width="50" max-width="50" :src="require('../assets/eyes.svg')"/>
                    </v-tab>
                    <v-tab value="mouth">
                      <v-img width="50" max-width="50" :src="require('../assets/mouth.svg')"/>
                    </v-tab>
                    <v-tab value="hair">
                      <v-img width="50" max-width="50" :src="require('../assets/hair.svg')"/>
                    </v-tab>
                    <v-tab value="hairColor">
                      <v-img width="30" max-width="30" :src="require('../assets/dye.svg')"/>
                    </v-tab>
                    <v-tab value="accessories">
                      <v-img width="40" max-width="40" :src="require('../assets/accessories.svg')"/>
                    </v-tab>
                    <v-tab value="bgColor">
                      <v-img width="50" max-width="50" :src="require('../assets/frame.svg')"/>
                    </v-tab>
                  </v-tabs>

                  <v-card-text>
                    <v-tabs-window v-model="tab">
                      <v-tabs-window-item value="skinColor">
                        <v-btn-toggle v-model="skinColor" variant="outlined"
                          class="d-flex flex-wrap justify-center align-center" style="width: 200%; height: 200%"
                          mandatory>
                          <v-btn value="8c5a2b" style="background: #8c5a2b;" rounded="xl" size="x-large"
                            class="ma-3 border-lg rounded-circle" width="100" height="100"></v-btn>
                          <v-btn value="a47539" style="background: #a47539;" rounded="xl" size="x-large"
                            class="ma-3 border-lg rounded-circle" width="100" height="100"></v-btn>
                          <v-btn value="c99c62" style="background: #c99c62;" rounded="xl" size="x-large"
                            class="ma-3 border-lg rounded-circle" width="100" height="100"></v-btn>
                          <v-btn value="e2ba87" style="background: #e2ba87;" rounded="xl" size="x-large"
                            class="ma-3 border-lg rounded-circle" width="100" height="100"></v-btn>
                          <v-btn value="efcc9f" style="background: #efcc9f;" rounded="xl" size="x-large"
                            class="ma-3 border-lg rounded-circle" width="100" height="100"></v-btn>
                          <v-btn value="f5d7b1" style="background: #f5d7b1;" rounded="xl" size="x-large"
                            class="ma-3 border-lg rounded-circle" width="100" height="100"></v-btn>
                          <v-btn value="ffe4c0" style="background: #ffe4c0;" rounded="xl" size="x-large"
                            class="ma-3 border-lg rounded-circle" width="100" height="100"></v-btn>
                        </v-btn-toggle>
                      </v-tabs-window-item>

                      <v-tabs-window-item value="eyes">
                        <div class="d-flex flex-row flex-wrap justify-center align-content-center">
                          <v-img class="mr-16 my-5" width="100" max-width="100"
                            :src="require('../assets/avatar/cheery.svg')" v-on:click="eyes = 'cheery'" />
                          <v-img class="ml-16 mr-16 my-5" width="100" max-width="100"
                            :src="require('../assets/avatar/starstruck.svg')" v-on:click="eyes = 'starstruck'" />
                          <v-img class="ml-16 mr-16 my-5" width="100" max-width="100"
                            :src="require('../assets/avatar/winking.svg')" v-on:click="eyes = 'winking'" />
                          <v-img class="ml-16 my-5" width="100" max-width="100"
                            :src="require('../assets/avatar/normal.svg')" v-on:click="eyes = 'normal'" />
                        </div>
                      </v-tabs-window-item>

                      <v-tabs-window-item value="mouth">
                        <div class="d-flex flex-row flex-wrap justify-center align-content-center">
                          <v-img class="ma-3" width="150" max-width="150" :src="require('../assets/avatar/braces.svg')"
                            v-on:click="mouth = 'braces'" />
                          <v-img class="ma-3" width="150" max-width="150"
                            :src="require('../assets/avatar/gapSmile.svg')" v-on:click="mouth = 'gapSmile'" />
                          <v-img class="ma-3" width="150" max-width="150" :src="require('../assets/avatar/kawaii.svg')"
                            v-on:click="mouth = 'kawaii'" />
                          <v-img class="ma-3" width="150" max-width="150"
                            :src="require('../assets/avatar/openedSmile.svg')" v-on:click="mouth = 'openedSmile'" />
                          <v-img class="ma-3" width="150" max-width="150"
                            :src="require('../assets/avatar/teethSmile.svg')" v-on:click="mouth = 'teethSmile'" />
                          <v-img class="ma-3" width="150" max-width="150"
                            :src="require('../assets/avatar/awkwardSmile.svg')" v-on:click="mouth = 'awkwardSmile'" />
                        </div>
                      </v-tabs-window-item>

                      <v-tabs-window-item value="hair">
                        <div class="d-flex flex-row flex-wrap justify-center align-content-center">
                          <v-img class="mx-3" width="130" max-width="130"
                            :src="require('../assets/avatar/curlyBob.svg')" v-on:click="hair = 'curlyBob'" />
                          <v-img class="mx-3" width="130" max-width="130"
                            :src="require('../assets/avatar/straightHair.svg')" v-on:click="hair = 'straightHair'" />
                          <v-img class="mx-3" width="130" max-width="130"
                            :src="require('../assets/avatar/shortHair.svg')" v-on:click="hair = 'shortHair'" />
                          <v-img class="mx-3" width="130" max-width="130"
                            :src="require('../assets/avatar/shavedHead.svg')" v-on:click="hair = 'shavedHead'" />
                          <v-img class="mx-3" width="130" max-width="130" :src="require('../assets/avatar/mohawk.svg')"
                            v-on:click="hair = 'mohawk'" />
                          <v-img class="mx-3" width="130" max-width="130"
                            :src="require('../assets/avatar/halfShavedHead.svg')"
                            v-on:click="hair = 'halfShavedHead'" />
                          <v-img class="mx-3" width="130" max-width="130" :src="require('../assets/avatar/froBun.svg')"
                            v-on:click="hair = 'froBun'" />
                          <v-img class="mx-3" width="130" max-width="130"
                            :src="require('../assets/avatar/curlyShortHair.svg')"
                            v-on:click="hair = 'curlyShortHair'" />
                          <v-img class="mx-3" width="130" max-width="130" :src="require('../assets/avatar/bunHair.svg')"
                            v-on:click="hair = 'bunHair'" />
                          <v-img class="mx-3" width="130" max-width="130"
                            :src="require('../assets/avatar/curlyBob.svg')" v-on:click="hair = 'curlyBob'" />
                          <v-img class="mx-3" width="130" max-width="130" :src="require('../assets/avatar/wavyBob.svg')"
                            v-on:click="hair = 'wavyBob'" />
                          <v-img class="mx-3" width="130" max-width="130" :src="require('../assets/avatar/bangs.svg')"
                            v-on:click="hair = 'bangs'" />
                          <v-img class="mx-3" width="130" max-width="130"
                            :src="require('../assets/avatar/bowlCutHair.svg')" v-on:click="hair = 'bowlCutHair'" />
                          <v-img class="mx-3" width="130" max-width="130"
                            :src="require('../assets/avatar/braids.svg')" v-on:click="hair = 'braids'" />
                        </div>
                      </v-tabs-window-item>

                      <v-tabs-window-item value="hairColor">
                        <v-btn-toggle v-model="hairColor" variant="outlined"
                            class="d-flex flex-wrap justify-center align-center" style="width: 200%; height: 200%"
                            mandatory>
                          <v-btn value="220f00" style="background: #220f00" rounded="xl" size="x-large"
                            class="mx-1 border-lg rounded-circle" width="100" height="100"></v-btn>
                          <v-btn value="238d80" style="background: #238d80" rounded="xl" size="x-large"
                            class="mx-1 border-lg rounded-circle" width="100" height="100"></v-btn>
                          <v-btn value="3a1a00" style="background: #3a1a00" rounded="xl" size="x-large"
                            class="mx-1 border-lg rounded-circle" width="100" height="100"></v-btn>
                          <v-btn value="605de4" style="background: #605de4" rounded="xl" size="x-large"
                            class="mx-1 border-lg rounded-circle" width="100" height="100"></v-btn>
                          <v-btn value="71472d" style="background: #71472d" rounded="xl" size="x-large"
                            class="mx-1 border-lg rounded-circle" width="100" height="100"></v-btn>
                          <v-btn value="d56c0c" style="background: #d56c0c" rounded="xl" size="x-large"
                            class="mx-1 border-lg rounded-circle" width="100" height="100"></v-btn>
                          <v-btn value="e2ba87" style="background: #e2ba87" rounded="xl" size="x-large"
                            class="mx-1 border-lg rounded-circle" width="100" height="100"></v-btn>
                          <v-btn value="e9b729" style="background: #e9b729" rounded="xl" size="x-large"
                            class="mx-1 border-lg rounded-circle" width="100" height="100"></v-btn>
                        </v-btn-toggle>
                      </v-tabs-window-item>

                      <v-tabs-window-item value="accessories">
                        <div class="d-flex flex-row flex-wrap justify-center align-content-center">
                          <v-btn class="pa-2 border-lg" rounded="xl" size="x-large"
                            v-on:click="accessories = ''">none</v-btn>
                          <v-img class="ml-16 mb-7" width="160" max-width="160"
                            :src="require('../assets/avatar/glasses.svg')" v-on:click="accessories = 'glasses'" />
                          <v-img class="ml-16 mb-7" width="160" max-width="160"
                            :src="require('../assets/avatar/catEars.svg')" v-on:click="accessories = 'catEars'" />
                          <v-img class="ml-16 mb-7" width="50" max-width="50"
                            :src="require('../assets/avatar/clownNose.svg')" v-on:click="accessories = 'clownNose'" />
                          <v-img class="ml-16 mb-7" width="160" max-width="160"
                            :src="require('../assets/avatar/faceMask.svg')" v-on:click="accessories = 'faceMask'" />
                          <v-img class="ml-16 mb-7" width="160" max-width="160"
                            :src="require('../assets/avatar/sailormoonCrown.svg')"
                            v-on:click="accessories = 'sailormoonCrown'" />
                          <v-img class="ml-16 mb-7" width="160" max-width="160"
                            :src="require('../assets/avatar/sunglasses.svg')" v-on:click="accessories = 'sunglasses'" />
                          <v-img class="ml-16 mb-7" width="160" max-width="160"
                            :src="require('../assets/avatar/sleepMask.svg')" v-on:click="accessories = 'sleepMask'" />
                          <v-img class="ml-16 mb-7" width="160" max-width="160"
                            :src="require('../assets/avatar/mustache.svg')" v-on:click="accessories = 'mustache'" />
                        </div>
                      </v-tabs-window-item>

                      <v-tabs-window-item value="bgColor">
                        <v-btn-toggle v-model="bgColor" variant="outlined"
                          class="d-flex flex-wrap justify-center align-center" style="width: 200%; height: 200%"
                          mandatory>
                          <v-btn value="b6e3f4" style="background: #b6e3f4" rounded="xl" size="x-large"
                            class="ma-3 border-lg rounded-circle" width="100" height="100"></v-btn>
                          <v-btn value="c0aede" style="background: #c0aede" rounded="xl" size="x-large"
                            class="ma-3 border-lg rounded-circle" width="100" height="100"></v-btn>
                          <v-btn value="d1d4f9" style="background: #d1d4f9" rounded="xl" size="x-large"
                            class="ma-3 border-lg rounded-circle" width="100" height="100"></v-btn>
                          <v-btn value="ffd5dc" style="background: #ffd5dc" rounded="xl" size="x-large"
                            class="ma-3 border-lg rounded-circle" width="100" height="100"></v-btn>
                          <v-btn value="ffdfbf" style="background: #ffdfbf" rounded="xl" size="x-large"
                            class="ma-3 border-lg rounded-circle" width="100" height="100"></v-btn>
                        </v-btn-toggle>
                      </v-tabs-window-item>
                    </v-tabs-window>
                  </v-card-text>

                </v-card>
              </v-col>
            </v-row>
          </template>

          <template v-slot:[`item.2`]>
            <v-row align="center" justify="space-around" no-gutters>
              <v-col cols="3">
                <v-avatar ref="avatar" :image="displayAvatar" size="100%"></v-avatar>
              </v-col>
              <v-col cols="8">
                <v-card flat width="950">
                    <v-form @submit.prevent>
                      <v-row no-gutters>
                        <v-col cols="3">
                          <v-date-input v-model="date" label="Date of Birth" prepend-icon="" variant="solo" :rules="[required]"></v-date-input>
                        </v-col>
                        <v-col cols="3">
                          <v-text-field v-model="pronouns" :rules="[required]" label="Pronouns" variant="solo"></v-text-field>
                        </v-col>
                        <v-col cols="6">
                          <v-text-field v-model="username" :rules="usernameRules" label="Username" variant="solo"></v-text-field>
                        </v-col>
                      </v-row>
                      <v-row no-gutters>
                        <v-col>
                          <v-text-field v-model="email" :rules="[required]" label="Email" variant="solo"></v-text-field>
                        </v-col>
                        <v-col>
                          <v-text-field v-model="password" :rules="usernameRules" label="Password" variant="solo"></v-text-field>
                        </v-col>
                      </v-row>
                      <div class="d-flex flex-wrap justify-center align-center">
                        <v-btn type="submit" v-on:click="login" color="yellow-darken-3" width="100">Login</v-btn>
                        <v-divider class="my-3"></v-divider>
                        <v-btn type="submit" v-on:click="loginWithGoogle" color="yellow-darken-3">Login with Google</v-btn>
                      </div>
                    </v-form>
                </v-card>
              </v-col>
            </v-row>
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
import { auth, db, } from "./Firebase.js";
import {
  signInWithEmailAndPassword,
  signInWithPopup,
  GoogleAuthProvider,
  setPersistence,
  browserLocalPersistence,
  updateProfile
} from "firebase/auth";
import { collection, doc, setDoc } from "firebase/firestore";
// avatar API
import { createAvatar } from '@dicebear/core';
import { bigSmile } from '@dicebear/collection';
// date input
import { VDateInput } from 'vuetify/labs/VDateInput';

// firebase
const usersCollectionRef = collection(db, "Users");

export default {
  name: "LoginView",
  components: {
    VDateInput,
  },
  data: () => ({
    tab: null,
    // avatar
    skinColor: "e2ba87",
    eyes: "cheery",
    mouth: "braces",
    hair: "curlyBob",
    hairColor: "605de4",
    accessories: "glasses",
    bgColor: "c0aede",
    // forms
    date: null,
    pronouns: "",
    username: "",
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
      console.log(avatar);
      return avatar;
    }
  },
  methods: {
    // form validation
    required(v) {
      return !!v || 'Field is required'
    },
    usernameCheck(v) {
      return /^(?=.{8,20}$)(?![.-])(?!.*[.]{2})[a-zA-Z0-9.-]+(?<![.])$/.test(v) || "Username must be 8-20 characters long. Avoid adding underscores, dashes, and periods."
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
      setPersistence(auth, browserLocalPersistence)
        .then(() => {
          const googleProvider = new GoogleAuthProvider();
          signInWithPopup(auth, googleProvider);
          // update user profile
          updateProfile(auth.currentUser, {
            displayName: this.username,
            photoURL: this.displayAvatar,
          });
          console.log("username and profile picture set");
          // store user in Firestore db
          setDoc(doc(usersCollectionRef, auth.currentUser.uid), {
            email: this.email,
            username: this.username,
            birthdate: this.date,
            pronouns: this.pronouns,
          });
          console.log("user stored");
        })
        .catch((error) => {
          console.log(error.code, error.message);
        });
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
  justify-center: center;
  margin: 25px;
}
</style>
