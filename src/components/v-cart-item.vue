<template>
  <div class="v-cart-item">
    <img class="image" :src="cart_item_data.image">
<!--      <img :src=" require('../assets/images/' + cart_item_data.images) " alt="">-->
    <div class="v-cart-item__info">
      <p>{{cart_item_data.name}}</p>
      <p>{{cart_item_data.price}}</p>
      <p>{{cart_item_data.article}}</p>
    </div>
    <div class="v-cart-item__quantity">
      <p>Количество:</p>
      <span class="quantity__tools">
        <span class="quantity__btn" @click="decrementItem">-</span>
        {{quantity}}
        <span class="quantity__btn" @click="incrementItem">+</span>
      </span>
      <br>
      <button @click="deleteFromCart" class="btn">Убрать с корзины</button>
    </div>
<!--    <button @click="deleteFromCart">Delete</button>-->

  </div>
</template>

<script>
export default {
  name: "v-cart-item",
  data(){
    return{
      quantity: 1
    }
  },
  props:{
    cart_item_data:{
      type: Object,
      default(){
        return{}
      }
    }
  },
  methods:{
    decrementItem(){
      if (this.quantity>0) {
        this.quantity--;
      }
    },
    incrementItem(){
      if (this.quantity<100) {
        this.quantity++;
      }
    },
    deleteFromCart(){
      this.$emit('deleteFromCart');
    }
  }
}
</script>

<style lang="scss">
.v-cart-item {
  display: flex;
  flex-wrap: nowrap;
  justify-content: space-between;
  align-items: center;
  box-shadow: 0 0 8px 0 #e0e0e0;
  padding: 16px;
  margin-bottom: 16px;
  .image {
    max-width: 50px;
  }

  .quantity__btn {
    cursor: pointer;
    font-size: 20px;
    margin: 0 5px;
  }
  .quantity__btn:hover{
    color: wheat;
  }
  .btn{
    padding: 10px 12px;
    background: none;
    border: #e0e0e0 1px solid;
    border-radius: 5px;
  }
  .btn:hover{
    background-color: wheat;
    border: white 1px solid;
    cursor: pointer;
  }

  .quantity__tools {
    user-select: none;
  }
}
</style>