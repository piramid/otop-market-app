<template>
  <div>
      <h1>Product</h1>
      <ul>
          <li v-for="pd in products" :key="pd.pid">
              {{pd.pid}} {{pd.name}} {{pd.img}}
          </li>
      </ul>

  </div>
</template>

<script>
export default {
    data() {
        return {
            products: []
        }
    },
    async created() {
        console.log('page load')
        let res = await this.$http.get('/product')
        console.log(res.data.product)
        this.products = res.data.product


    },
  
}
</script>

