<template>
  <v-row dense>
    <template v-for="cat in cats">
      <v-col :key="cat.uuid" cols="12" lg="6" md="12">
        <cat-item :cat="cat" />
      </v-col>
    </template>
  </v-row>
</template>

<script>
import CatItem from '@/components/CatItem.vue'

export default {
  comments: {
    CatItem,
  },
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
      this.cats = response.data.results
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
