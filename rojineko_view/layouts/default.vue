<template>
  <v-app>
    <v-app-bar fixed app flat color="blue">
      <v-toolbar-title :class="$style.toolbar_title" v-text="title" />
      <v-spacer />
    </v-app-bar>
    <v-main>
      <v-container>
        <Nuxt />
      </v-container>
    </v-main>

    <v-footer :absolute="!fixed" app>
      <span>&copy; {{ new Date().getFullYear() }}</span>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  name: 'DefaultLayout',
  data() {
    return {
      title: 'ロジねこビュー',
    }
  },
}
</script>

<style lang="scss" module>
.toolbar_title {
  color: #ffffff;
  font-weight: bold;
}
</style>
