<template>
  <div v-for="(item, index) in selectedProduct" :key="index">
    <img alt="Vue logo" :src="imagePath(item.image)" />
    <h1 class="item-name">{{ item.name }}</h1>
    <span class="price">Price : {{ item.price }}</span>
  </div>
</template>

<script>
export default {
  name: "ProductDetail",
  props: {
    selectedProduct: {
      type: Array,
      default: null,
    },
  },
  components: {},

  setup() {
    const imagePath = (image) => {
      return require("../assets" + image);
    };
    return { imagePath };
  },
};
</script>

<style scoped>
.item-name {
  color: #04a64a;
}
.price {
  font-size: 25px;
  color: #aaeff7;
}
</style>
