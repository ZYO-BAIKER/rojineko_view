<template>
  <v-row></v-row>
</template>

<script>
export default {
  async created() {
    try {
      const response = await this.$axios.get(
        'https://livlog.xyz/webapi/cats.json'
      )
      console.log(response)
    } catch (err) {
      const res = err.response
      console.log(res)
    } finally {
      // ここに共通の最終処理を書く
    }
  },
}
</script>
