<template>
  <div>
    <v-container>
      <v-row align="center" justify="center" style="height: 80vh;" no-gutters>
        <v-stepper :items="['Create your Avatar', 'Register your account', 'Begin your journey']"
          bg-color="teal-lighten-5" class="border-lg border-surface-variant" min-width="1500">

          <template v-slot:[`item.1`]>
            <v-row align="center" justify="space-around" no-gutters>
              <v-col cols="3">
                <v-avatar ref="avatar" :image="displayAvatar" size="90%"></v-avatar>
                <v-text-field v-model="username" :rules="[required, usernameRules]" label="Username" variant="solo"
                  class="mt-5"></v-text-field>
                <v-row>
                  <v-col>
                    <v-date-input v-model="date" label="Date of Birth" prepend-icon="" variant="solo"
                      required></v-date-input>
                  </v-col>
                  <v-col>
                    <v-text-field v-model="pronouns" :rules="[required]" label="Pronouns" variant="solo"></v-text-field>
                  </v-col>
                </v-row>

              </v-col>

              <v-col cols="8">
                <v-card color="light-green-lighten-4" class="border-lg border-accent" height="500" width="950">

                  <v-tabs v-model="tab" align-tabs="center" variant="text" bg-color="yellow-darken-3"
                    class="border-b-lg border-surface-variant" height="70">
                    <v-tab value="skinColor">SKIN</v-tab>
                    <v-tab value="eyes">EYES</v-tab>
                    <v-tab value="mouth">MOUTH</v-tab>
                    <v-tab value="hair">HAIR</v-tab>
                    <v-tab value="hairColor">DYE</v-tab>
                    <v-tab value="accessories">ACCESSORIES</v-tab>
                    <v-tab value="bgColor">BACKGROUND</v-tab>
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
                          <v-img class="mx-3" width="130" max-width="130" :src="require('../assets/avatar/braids.svg')"
                            v-on:click="hair = 'braids'" />
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
                <v-avatar ref="avatar" :image="displayAvatar" size="85%"></v-avatar>
              </v-col>
              <v-col cols="8">
                <v-card flat width="950">
                  <v-form @submit.prevent>
                    <v-row>
                      <v-col cols="3">
                        <v-date-input v-model="date" label="Date of Birth" prepend-icon="" variant="solo"
                          :rules="[required]"></v-date-input>
                      </v-col>
                      <v-col cols="3">
                        <v-text-field v-model="pronouns" :rules="[required]" label="Pronouns"
                          variant="solo"></v-text-field>
                      </v-col>
                      <v-col cols="6">
                        <v-text-field v-model="username" :rules="usernameRules" label="Username"
                          variant="solo"></v-text-field>
                      </v-col>
                    </v-row>
                    <v-row style="margin-top: -15px;">
                      <v-col>
                        <v-text-field v-model="email" :rules="[emailCheck]" label="Email" variant="solo"></v-text-field>
                      </v-col>
                      <v-col>
                        <v-defaults-provider :defaults="{'VIcon':{'color':'success'}}">
                          <v-text-field
                            v-model="password"
                            :append-icon="showPassword ? mdiEye : mdiEyeOff"
                            :rules="usernameRules"
                            :type="showPassword ? 'text' : 'password'"
                            hint="At least 8 characters"
                            label="Password"
                            variant="solo"
                            name="input-10-1"
                            counter
                            @click:append="showPassword = !showPassword"
                          ></v-text-field>
                        </v-defaults-provider>
                      </v-col>
                    </v-row>
                    <div class="d-flex flex-wrap justify-center align-center">
                      <v-btn type="submit" v-on:click="login" color="yellow-darken-3" width="100">Login</v-btn>
                      <v-divider class="my-3"></v-divider>
                      <v-btn type="submit" v-on:click="loginWithGoogle" color="yellow-darken-3">Login with
                        Google</v-btn>
                    </div>
                  </v-form>
                </v-card>
              </v-col>
            </v-row>
          </template>

          <template v-slot:[`item.3`]>
            <img :src="AppLogo" alt="SIKA" width="200"/>
            <h1>Welcome to SIKA!</h1>
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
  createUserWithEmailAndPassword,
  signInWithEmailAndPassword,
  signInWithPopup,
  GoogleAuthProvider,
  setPersistence,
  browserLocalPersistence,
  updateProfile,
} from "firebase/auth";
import { collection, doc, setDoc } from "firebase/firestore";
// avatar API
import { createAvatar } from '@dicebear/core';
import { bigSmile } from '@dicebear/collection';
// date input
import { VDateInput } from 'vuetify/labs/VDateInput';
// svg icon
import AppLogo from '../assets/sika-logo-3.svg';
// icons
import SvgIcon from '@jamescoyle/vue-icon';
import { mdiEye, mdiEyeOff } from '@mdi/js';

// get Users collection from database
const usersCollectionRef = collection(db, "Users");

export default {
  name: "LoginView",
  components: {
    VDateInput,
  },
  setup() {
    return {
      AppLogo,
      SvgIcon,
    };
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
    email: "",
    password: "",
    showPassword: false,
    // icon
    mdiEye: mdiEye,
    mdiEyeOff: mdiEyeOff,
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
    emailCheck(v) {
      return /.+@.+\..+/.test(v) || "Email is invalid."
    },
    login() {
      // store login credentials
      const email = this.email;
      const password = this.password;
      createUserWithEmailAndPassword(email, password)
        // if user doesn't exist, create account
        .then(() => {
          // update user profile
          updateProfile(auth.currentUser, {
            displayName: this.username,
            photoURL: this.displayAvatar,
          });
          console.log("username and profile picture set");
          // store user in Firestore db at id: user ID
          setDoc(doc(usersCollectionRef, auth.currentUser.uid), {
            email: this.email,
            username: this.username,
            birthdate: this.date,
            pronouns: this.pronouns,
          });
          console.log("user stored");
        })
        .catch(error => {
          switch (error.code) {
            // if account exists, log in with credentials
            case 'auth/email-already-in-use':
              signInWithEmailAndPassword(auth, email, password);
              // set user browser session
              setPersistence(auth, browserLocalPersistence)
                .then(() => {
                  // go to home page
                  this.$router.push("/");
                })
                .catch((error) => {
                  console.error(error);
                });
              break;
            case 'auth/invalid-email':
              console.log(`Email address ${this.state.email} is invalid.`);
              break;
            case 'auth/operation-not-allowed':
              console.log(`Error during sign up.`);
              break;
            case 'auth/weak-password':
              console.log('Password is not strong enough. Add additional characters including special characters and numbers.');
              break;
            default:
              console.log(error.message);
              break;
          }
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

.v-input__icon--append .v-icon { 
  color: purple;
}
</style>
