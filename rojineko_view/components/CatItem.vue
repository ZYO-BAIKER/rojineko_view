<template>
  <div :class="$style.container">
    <div :key="cat.uuid" :class="$style.cat_container">
      <img
        :src="cat.url"
        :alt="cat.uuid"
        :class="[
          $style.image,
          { [$style.small]: $vuetify.breakpoint.mdAndDown },
        ]"
      />

      <div :class="$style.info_container">
        <div>
          <span :class="$style.label">撮影場所:</span> {{ cat.address }}
        </div>
        <div>
          <span :class="$style.label">撮影日:</span>
          {{ cat.createDate | moment }}
        </div>
      </div>
      <v-divider></v-divider>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    cat: {
      type: Object,
      default: null,
    },
  },
}
</script>

<style lang="scss" module>
.container {
  .cat_container {
    display: flex;
    flex-flow: column;
    align-items: center;
    margin-bottom: 16px;
    border-bottom: 1px solid #ddd;

    .image {
      max-width: 100%;
      height: 500px;
      object-fit: contain;

      &.small {
        height: unset;
        max-height: 500px;
      }
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
