<template>
  <v-row></v-row>
</template>

<script>
export default {
  data() {
    return {
      cats: [],
    }
  },
  async created() {
    try {
      const response = await this.$axios.get(
        'https://livlog.xyz/webapi/cats.json'
      )
      this.cats = response.data
    } catch (err) {
      const res = err.response
      console.log(res)
      alert(res)
    } finally {
      // ここに共通の最終処理を書く
    }
  },
}
</script>
