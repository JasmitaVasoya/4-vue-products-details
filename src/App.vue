<template>
  <HeaderComponent></HeaderComponent>
  <component
    :is="activeComponent"
    @emitProduct="emitProduct"
    :selectedProduct="selectedProduct"
  ></component>
  <div v-if="!isCookie && isShowCookieNote">
    <h1>We use cookie</h1>
    <button @click="onAgree">I agree</button>
    <button @click="onNotAgree">Not agreed</button>
  </div>
  <FooterComponent></FooterComponent>

</template>

<script>
import FooterComponent from "./components/FooterComponent.vue";
import HeaderComponent from "./components/HeaderComponent.vue";
import MainProduct from "./components/MainProduct.vue";
import ProductList from "./components/ProductList.vue";
import SubProduct from "./components/SubProduct.vue";
import ProductDetail from "./components/ProductDetail.vue";
import { ref, onMounted } from "vue";

export default {
  components: {
    FooterComponent,
    HeaderComponent,
    MainProduct,
    ProductList,
    SubProduct,
    ProductDetail,
  },
  setup() {
    const activeComponent = ref("ProductList");
    const selectedProduct = ref(null);
    const isCookie = ref(true);
    const isShowCookieNote = ref(true);
    const emitProduct = (product, component) => {
      selectedProduct.value = product;
      activeComponent.value = component;
    };
    const onAgree = () => {
      isShowCookieNote.value = false;
      localStorage.setItem("setCookie", true);
    };
    const onNotAgree = () => {
      isShowCookieNote.value = false;
    };
    onMounted(() => {
      const getStoredData = localStorage.getItem("setCookie");

      isCookie.value = getStoredData;
    });
    return {
      activeComponent,
      emitProduct,
      selectedProduct,
      isShowCookieNote,
      onAgree,
      isCookie,
      onNotAgree,
    };
  },
};
</script>

<style>
#app {
background : #495057;
  text-align: center;
  color: #2c3e50;
}
</style>
