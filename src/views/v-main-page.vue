<template>
  <v-header @changePage="changePage"></v-header>
  <div class="container">
    <v-catalog
        @addToCart="addToCart"
        :cart="cart"
        v-if="page==1"
    ></v-catalog>
    <VCart
        v-if="page==2"
        :cart_data="CART"
        :basket = basket
        @removeCart="removeCart"
    />
  </div>
</template>

<script>

import VHeader from "@/components/v-header";
import VCart from "@/components/v-cart";
import {mapActions, mapGetters} from "vuex";
import VCatalog from "@/components/v-catalog";

export default {
  name: "v-main-page",
  components: {VCatalog, VCart, VHeader},
  data(){
    return{
      page: 1,
      basket: [],
      cart: {}
    }
  },
  methods:{
    ...mapActions([
      'DEL_TO_CART'
    ]),
    changePage(page){
      this.page = page;
    },
    addToCart(item){
      this.basket.push(item)
      console.log(this.basket)
    },
    removeCart(cart){
      this.cart = cart;
      // this.DEL_TO_CART({cart})
    }
  },
  computed:{
    ...mapGetters(['CART'])
  }
}
</script>

<style scoped>
.container{
  max-width: 900px;
  margin: 0 auto;
}
</style>