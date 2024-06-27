<template class="rounded-0">
  <v-layout class="d-flex justify-center align-center">
    <v-bottom-navigation grow>
      <v-btn value="login" to="/login">
        <RouterLink to="/login">
          <svg-icon type="mdi" :path="mdiAccount"></svg-icon>
        </RouterLink>
      </v-btn>

      <v-btn value="home" to="/">
        <RouterLink to="/">
          <svg-icon type="mdi" :path="mdiPalette"></svg-icon>
        </RouterLink>
      </v-btn>

      <v-btn value="register" to="/register">
        <RouterLink to="/register">
          <svg-icon type="mdi" :path="mdiBook"></svg-icon>
        </RouterLink>
      </v-btn>

      <v-btn value="register" to="/register">
        <RouterLink to="/register">
          <svg-icon type="mdi" :path="mdiMessage"></svg-icon>
        </RouterLink>
      </v-btn>
    </v-bottom-navigation>

    <main>
      <RouterView />
    </main>
  </v-layout>
</template>

<script>
// icons
import SvgIcon from '@jamescoyle/vue-icon'
import { mdiAccount, mdiPalette, mdiBook, mdiMessage } from '@mdi/js'

export default {
  name: "App",
  components: {
    SvgIcon
  },
  data: () => ({
    mdiAccount: mdiAccount,
    mdiPalette: mdiPalette,
    mdiBook: mdiBook,
    mdiMessage: mdiMessage,
  }),
};
</script>

<style lang="scss">
@font-face {
  font-family: 'LoRes15OT-Bold';
  src: url('assets/fonts/LoRes15OT-Bold.ttf');
}

// @font-face {
//   font-family: 'LoRes15OT-AltOakland-Bold';
//   src: url('assets/fonts/LoRes15OT-AltOakland-Bold.ttf');
// }

#app {
  font-family: 'LoRes15OT-Bold';
  font-size: 1.5em;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
