<template>
  <div class="row">
    <div
      v-for="(item, index) in selectedProduct"
      :key="index"
      @click="onClickProductDetail(item)"
      class="column"
    >
      <img alt="Vue logo" :src="imagePath(item[0].image)" class="img" />
      <div class="list">{{ item[0].name }}</div>
    </div>
  </div>
</template>

<script>
export default {
  name: "SubProduct",
  props: {
    selectedProduct: {
      type: Array,
      default: null,
    },
  },
  components: {},

  setup(props, context) {
    const onClickProductDetail = (product) => {
      context.emit("emitProduct", product, "ProductDetail");
    };
    const imagePath = (image) => {
      return require("../assets" + image);
    };
    return {
      onClickProductDetail,
      imagePath,
    };
  },
};
</script>

<style></style>
