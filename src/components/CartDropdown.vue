<template>
  <div class="dropdown-clip" v-if="cart.length > 0">
    <transition name="dropdown">
      <div
        v-if="displayCart"
        class="list-group bg-white"
        aria-labelledby="cartDropdown"
      >
        <div v-for="(item, index) in cart" :key="index">
          <div class="dropdown-item-text text-nowrap text-right align-middle">
            <span class="badge bg-success align-text-top mr-1">
              {{ item.qty }}</span
            >
            {{ item.product.name }}
            <b>
              <currency :amt="item.qty * Number(item.product.price)"></currency>
            </b>
            <button
              @click.stop="deleteItem(index)"
              class="btn btn-small btn-danger ml-2"
            >
              -
            </button>
          </div>
        </div>
        <router-link
          class="btn btn-sm btn-success text-white float-right mr-2 mt-2"
          to="/checkout"
          >Checkout</router-link
        >
      </div>
    </transition>
  </div>
</template>

<script>
import Currency from "./Currency";
export default {
  props: ["cart", "displayCart"],
  inject: ["delete"],
  components: {
    Currency,
  },
  methods: {
    deleteItem(i) {
      this.delete(i);
    },
  },
  computed: {
    console: () => console.log(this.cart),
  },
};
</script>

<style>
.dropdown-clip {
  overflow: hidden;
}

.dropdown-enter-active,
.dropdown-leave-active {
  transition: all 0.5s ease-in-out;
  transform: auto;
}

.dropdown-enter-from,
.dropdown-leave-to {
  opacity: 0;
  transform: translateY(-300px);
}
</style>
