<template>
  <div class="row">
    <div
      v-for="(item, index) in Object.values(categoryData)"
      :key="index"
      @click="onClickProduct(item.subProduct)"
      class="column"
    >
      <img alt="Vue logo" :src="imagePath(item.image)" class="img" /><span class="list">
        {{ item.name }}
      </span>
    </div>
  </div>
</template>

<script>
import categoryData from "../categoryData.json";

export default {
  name: "ProductList",
  components: {},
  emits: ["emitProduct"],
  setup(props, context) {
    const onClickProduct = (product) => {
      context.emit("emitProduct", product, "MainProduct");
    };
    const imagePath = (image) => {
      return require("../assets" + image);
    };
    return {
      categoryData,
      onClickProduct,
      imagePath,
    };
  },
};
</script>

<style scoped>
.list {
  margin-top: 11px;
}
.column {
  display: flex;
  float: left;
  width: 18.33%;
  padding: 25px;
  text-align: center;
  font-size: 25px;
  cursor: pointer;
  color: #04a64a;
  margin-left: 20%;
}
.img {
  margin-right: 20px;
}

/* Clear floats after the columns */
.row:after {
  content: "";
  display: table;
  clear: both;
}

* {
  box-sizing: border-box;
}
</style>
