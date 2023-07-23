<template>
  <header>
    <div class="inner">
      <div class="logo">
        Logo
      </div>
      <nav>
        <p @click="changePage(1)">Товары</p>
        <p @click="changePage(2)">Корзина</p>
      </nav>
    </div>
  </header>
</template>

<script>
export default {
  name: "v-header",
  data(){
    return{
      page: 1
    }
  },
  methods:{
    changePage(page){
      this.page = page;
      this.$emit('changePage', page);
    }
  }
}
</script>

<style lang="scss" scoped>
header{
  width: 100%;
  padding: 20px 0;
  box-shadow: 0 0 8px 0 #e0e0e0 ;
  margin-bottom: 40px;
  .inner{
    display: flex;
    padding: 0 20px;
    justify-content: space-between;
    .logo{
      cursor: pointer;
    }
    nav{
      display: flex;
      p{
        margin-left: 12px;
      }
      p:hover{
        cursor: pointer;
        color: wheat;
      }
    }
  }
}
</style>