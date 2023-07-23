<template>
  <div class="v-cart">
    <h1>Cart</h1>
    <VCartItem
      v-for="(item, index) in cart_data"
      :key="item.article"
      :cart_item_data="item"
      :basket="item"
      @deleteFromCart="deleteFromCart(index)"
    />
  </div>
</template>

<script>
import VCartItem from "@/components/v-cart-item";
import {mapActions} from "vuex";

export default {
  name: "v-cart",
  components: {VCartItem},
  props:{
    cart_data:{
      type: Array,
      default() {
        return [];
      }
    },
    basket:{
      type: Array
    }
  },
  methods:{
    addToCart(basket){
      this.basket = basket;
      console.log(basket)
    },
    ...mapActions([
      'DEL_TO_CART'
        ]),
    deleteFromCart(index){
      this.DEL_TO_CART(index);
    }
  }
}
</script>

<style lang="scss" scoped>
.v-cart{

}
</style>