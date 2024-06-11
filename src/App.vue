<template>
  <v-layout class="d-flex justify-center align-center">
    <v-bottom-navigation grow>

      <v-btn value="home" to="/">
        <RouterLink to="/">
          <svg-icon type="mdi" :path="mdiHomeVariant"></svg-icon>
        </RouterLink>
      </v-btn>

      <v-btn value="login" to="/login">
        <v-icon>mdi-heart</v-icon>

        <RouterLink to="/login">Login</RouterLink>
      </v-btn>

      <v-btn value="register" to="/register">
        <v-icon>mdi-map-marker</v-icon>
        <RouterLink to="/register">Register</RouterLink>
      </v-btn>
    </v-bottom-navigation>

    <main><RouterView /></main>
  </v-layout>
</template>

<script>
import SvgIcon from '@jamescoyle/vue-icon'
import { mdiHomeVariant, mdiLoginVariant, } from '@mdi/js'



export default {
  name: "App",
  components: {
    SvgIcon
  },
  data() {
    return {
      mdiHomeVariant: mdiHomeVariant,
      mdiLoginVariant: mdiLoginVariant ,
    }
  },
};
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
