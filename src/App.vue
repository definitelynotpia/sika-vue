<template>
  <v-layout class="d-flex justify-center align-center">
    <v-bottom-navigation grow>

      <v-btn value="home" to="/">
        <RouterLink to="/">
          <svg-icon type="mdi" :path="mdiHomeVariant"></svg-icon>
        </RouterLink>
      </v-btn>

      <v-btn value="login" to="/login">
        <RouterLink to="/login">
          <svg-icon type="mdi" :path="mdiAccount"></svg-icon>
        </RouterLink>
      </v-btn>

      <v-btn value="register" to="/register">
        <RouterLink to="/register">
          <svg-icon type="mdi" :path="mdiHomeVariant"></svg-icon>
        </RouterLink>
      </v-btn>
    </v-bottom-navigation>

    <main><RouterView /></main>
  </v-layout>
</template>

<script>
// icons
import SvgIcon from '@jamescoyle/vue-icon'
import { mdiHomeVariant, mdiLoginVariant, mdiAccount } from '@mdi/js'

export default {
  name: "App",
  components: {
    SvgIcon
  },
  data() {
    return {
      mdiHomeVariant: mdiHomeVariant,
      mdiLoginVariant: mdiLoginVariant,
      mdiAccount: mdiAccount,
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
}
</style>
