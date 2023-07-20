<template>
  <div class="row">
    <div
      v-for="(item, index) in selectedProduct"
      :key="index"
      @click="onClickMainProduct(item.subProduct)"
      class="column"
    >
      <img alt="Vue logo" :src="imagePath(item.image)" class="img" />
      <div class="list">
        {{ item.name }}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "MainProduct",
  props: {
    selectedProduct: {
      type: Array,
      default: null,
    },
  },
  components: {},

  setup(props, context) {
    const onClickMainProduct = (product) => {
      context.emit("emitProduct", product, "SubProduct");
    };
    const imagePath = (image) => {
      return require("../assets" + image);
    };
    return {
      onClickMainProduct,
      imagePath,
    };
  },
};
</script>

<style></style>
