<template>
  <div v-for="(item, index) in selectedProduct" :key="index">
    <img alt="Vue logo" :src="imagePath(item.image)" />
    <button @click="onClickMainProduct(item.subProduct)">
      {{ item.name }}
    </button>
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
