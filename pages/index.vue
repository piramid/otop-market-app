<template>
<div align="center">
    <br>
  <img src="Otop-Content.jpg" alt="" height="80%" width="80%"><br>
  <v-btn color="success" @click="gotoTest02">เข้าโปรแกรม</v-btn>
</div>
</template>

<script>
export default {
  methods: {
    gotoTest02() {
      this.$router.push('/product-list')
    }
  }
}
</script>
