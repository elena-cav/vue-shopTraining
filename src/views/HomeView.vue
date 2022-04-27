<template>
  <section class="container">
    <range-selector v-model="max" :products="filteredProducts" />
    <products-list :products="filteredProducts" />
  </section>
</template>

<script>
// @ is an alias to /src
import ProductsList from "../components/ProductsList.vue";
import RangeSelector from "../components/RangeSelector.vue";

export default {
  name: "HomeView",
  data() {
    return {
      max: 50,
      cart: [],
    };
  },
  components: {
    RangeSelector,
    ProductsList,
  },
  props: ["products"],
  computed: {
    filteredProducts() {
      return this.products.filter((item) => item.price < Number(this.max));
    },
  },
};
</script>
