<template>
  <div v-for="(item, index) in selectedProduct" :key="index">
   <img alt="Vue logo" :src="imagePath(item[0].image)">
    <button @click="onClickProductDetail(item)">{{ item[0].name}}</button>
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

  setup(props,context) {
    
    const onClickProductDetail = (product) => {
        context.emit("emitProduct", product,"ProductDetail");
    };
     const imagePath = (image)=>{
return require('../assets'+image)
    }
    return {
      onClickProductDetail,imagePath
    };
  },
};
</script>

<style></style>
