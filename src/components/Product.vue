<template>
  <div class="col-2 m-auto">
    <button @click="addItem" class="btn btn-success">+</button>
  </div>
  <div class="col-sm-4">
    <img class="img-fluid d-block" :src="item.image" :alt="item.name" />
  </div>
  <div class="col">
    <h3 class="text-primary">{{ item.name }}</h3>
    <p class="mb-0">{{ item.description }}</p>
    <div class="h5 float-right">
      <span class="label"></span><currency :amt="item.price"></currency>
    </div>
  </div>
</template>

<script>
import Currency from "@/components/Currency.vue";
export default {
  inject: ["add"],
  props: ["item"],
  methods: {
    addItem() {
      this.add(this.item);
    },
  },
  components: {
    Currency,
  },
};
</script>
