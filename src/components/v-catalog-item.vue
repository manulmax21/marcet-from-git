<template>
  <div class="v-catalog-item">
    <img class="v-catalog-item__image" :src="product_data.image" alt="img"/>
    <p class="v-catalog-item__name">{{product_data.name}}</p>
    <p class="v-catalog-item__price">Price: {{product_data.price}} Р.</p>
    <button class="v-catalog-item__btn" @click="addToCart">add to basket</button>
  </div>
</template>

<script>
export default {
  name: "v-catalog-item",
  props: {
    product_data: {
      type: Object,
      default() {
        return {}
      }
    }
  },
  methods:{
    addToCart(){
      this.$emit('addToCart', this.product_data);
    }
  }
}
</script>

<style lang="scss">
@import "src/assets/styles/styles";

.v-catalog-item {
  box-shadow: 0 0 8px 0 #e0e0e0;
  padding: 16px;
  margin-bottom: 16px;
  &__btn{
    padding: 10px 12px;
    background: none;
    border: #e0e0e0 1px solid;
    border-radius: 5px;
  }
  &__btn:hover{
    background-color: wheat;
    border: white 1px solid;
    cursor: pointer;
  }
  &__image {
    width: 100px;
  }
}
</style>