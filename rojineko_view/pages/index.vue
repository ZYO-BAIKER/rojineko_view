<template>
  <div>
    <template v-for="cat in cats">
      <cat-item :key="cat.uuid" :cat="cat" />
    </template>
  </div>
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
