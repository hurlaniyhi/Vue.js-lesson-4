<template>
  <div id="product-list-one">
    <h2>Product List One</h2>
    <ul>
        <li v-bind:key="product" v-for="product in saleProducts">
            <span class="name">{{product.name}}</span>
             <span class="price">${{product.price}}</span>
        </li>
    </ul>
    <button @click="reduceIt(4)">Reduce Price</button>
   
  </div>
</template>

<script>
export default {

  data () {
    return {
     
    }
  },

  computed: {
      products(){
          return this.$store.state.products
      },
      saleProducts(){
          return this.$store.getters.saleProducts
      }
  },

  methods: {
      reduceIt: function (amount){
        //   this.$store.commit('reducePrice', amount)  // when using mutation directly

        this.$store.dispatch('reduceThePrice', {amount, router: this.$router}) // when using Action
        //this.$router.push({path: 'next'})
      }
  }
}

</script>

<style scoped>

#product-list-one{
    background: #FFF8B1;
    box-shadow: 1px 2px 3px rgba(0,0,0, 0.2);
    margin-bottom: 30px;
    padding: 10px 20px;
}
#product-list-one ul{
    padding: 0;
   
}
#product-list-one li{
    display: inline-block;
    margin-right: 10px;
    margin-top: 10px;
    padding: 20px;
    background: rgba(255,255,255,0.7);
}
.price{
    font-weight: bold;
    color: #E8800C;
}

</style>
