<template>
  <div class="v-catalog">
<!--      //v-for="product of this.$store.state.products"-->

        <VCatalogItem
          v-for="product of PRODUCTS"
          :key="product.article"
          v-bind:product_data="product"
          @addToCart="addToCart"
        />

  </div>
</template>

<script>
import VCatalogItem from "@/components/v-catalog-item";
import {mapActions, mapGetters} from "vuex";

export default {
  name: "v-catalog",
  components: {VCatalogItem},
  props:{
    cart:{
      type: Object
    }
  },
  data(){
    return{
      basket: {},
    }
  },
  computed: {
    ...mapGetters ([
        'PRODUCTS'
    ]),
  },
  methods: {
    ...mapActions([
        'GET_PRODUCTS_FROM_API',
        'ADD_TO_CART'
    ]),
    addToCart(data){
      this.ADD_TO_CART(data);
      this.basket = data;
      this.$emit('addToCart', this.basket)
    }
  },
  mounted() {
    this.GET_PRODUCTS_FROM_API()
    .then((response)=>{
      if (response.data){
        console.log('data arrived!')
      }
    })
  }
}
</script>

<style lang="scss">
.v-catalog {
  display: grid;
  grid-template-columns: repeat(3, 200px);
  justify-content: space-between;
  grid-row-gap: 5px;
  grid-column-gap: 5px;
  position: relative;
  //&__list {
  //  display: flex;
  //  flex-wrap: wrap;
  //  justify-content: space-between;
  //  align-items: center;
  //}
  .item_catalog{
    height: 200px;
    background-color: #eee;
  }
}
</style>