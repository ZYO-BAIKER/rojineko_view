<template>
  <div :class="$style.container">
    <template v-for="cat in cats">
      <div :key="cat.uuid" :class="$style.cat_container">
        <img :src="cat.url" :alt="cat.uuid" :class="$style.image" />

        <div :class="$style.info_container">
          <div>
            <span :class="$style.label">撮影場所:</span> {{ cat.address }}
          </div>
          <div>
            <span :class="$style.label">撮影日:</span> {{ cat.createDate }}
          </div>
        </div>
        <v-divider></v-divider>
      </div>
    </template>
  </div>
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

<style lang="scss" module>
.container {
  .cat_container {
    padding-bottom: 16px;
    margin-bottom: 16px;

    .image {
      max-width: 100%;
      max-height: 500px;
      object-fit: contain;
    }
    .info_container {
      padding: 16px 0;

      .label {
        font-weight: bold;
        width: 80px;
        display: inline-block;
      }
    }
  }
}
</style>
