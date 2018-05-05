<template>
  <v-layout row>
    <v-flex xs12 sm6 offset-sm3>
      <v-card>
        <v-card-media :src="products.img" height="300px">
          <v-layout column class="media">
            <v-spacer></v-spacer>
            <v-card-title class="white--text pl-5 pt-5">
              <div class="display-1 pl-5 pt-5" style="color:yellow;">{{products.name}}</div>
            </v-card-title>
          </v-layout>
        </v-card-media>
        <v-list two-line>
          <v-list-tile @click="doM1">
            <v-list-tile-action>
              <v-icon color="indigo">shopping_cart</v-icon>
            </v-list-tile-action>
            <v-list-tile-content>
              <v-list-tile-title>{{products.pid}}</v-list-tile-title>
              <v-list-tile-sub-title>รหัสสินค้า</v-list-tile-sub-title>
            </v-list-tile-content>
            <v-list-tile-action>
              <v-icon>chat</v-icon>
            </v-list-tile-action>
          </v-list-tile>
          <v-list-tile @click="doM2">
            <v-list-tile-action></v-list-tile-action>
            <v-list-tile-content>
              <v-list-tile-title>{{products.name}}</v-list-tile-title>
              <v-list-tile-sub-title>ชื่อสินค้า</v-list-tile-sub-title>
            </v-list-tile-content>
            <v-list-tile-action>
              <v-icon>chat</v-icon>
            </v-list-tile-action>
          </v-list-tile>
          <v-divider inset></v-divider>
          <v-list-tile @click="doM3">
            <v-list-tile-action>
              <v-icon color="indigo">details</v-icon>
            </v-list-tile-action>
            <v-list-tile-content>
              <v-list-tile-title>{{products.detail}}</v-list-tile-title>
              <v-list-tile-sub-title>รายละเอียดสินค้า</v-list-tile-sub-title>
            </v-list-tile-content>
          </v-list-tile>
          <v-list-tile @click="doM4">
            <v-list-tile-action></v-list-tile-action>
            <v-list-tile-content>
              <v-list-tile-title>{{products.price}} บาท</v-list-tile-title>
              <v-list-tile-sub-title>ราคาสินค้า</v-list-tile-sub-title>
            </v-list-tile-content>
          </v-list-tile>
          <v-divider inset></v-divider>
          <v-list-tile @click="doM5">
            <v-list-tile-action>
              <v-icon color="indigo">check_circle</v-icon>
            </v-list-tile-action>
            <v-list-tile-content>
              <v-list-tile-title>
              <v-icon v-if="products.star1 == 1 && products.star2 == 0 && products.star3 == 0" color="pink">star star_border star_border</v-icon>
              <v-icon v-else-if="products.star1 == 1 && products.star2 == 1 && products.star3 == 0" color="pink">star star star_border</v-icon>
              <v-icon v-else-if="products.star1 == 1 && products.star2 == 1 && products.star3 == 1" color="pink">star star star</v-icon>
              </v-list-tile-title>
              <v-list-tile-sub-title>คุณภาพสินค้า</v-list-tile-sub-title>
            </v-list-tile-content>
          </v-list-tile>
        </v-list>
      </v-card>
    </v-flex>
  </v-layout>
</template>

<script>
export default {
  data () {
      return {
        products: [],
            
//           items: [
//               {pid: 1001, name: 'น้ำพริกกุ้งเสียบ', icon1: true, icon2: true, icon3: true, title: 'น้ำพริกกุ้งเสียบ', avatar: 'pic001.jpg'},
//               {pid: 1002, name: 'น้ำว่านกาบหอย',  icon1: true, icon2: false, icon3: false, title: 'น้ำว่านกาบหอย', avatar: 'pic002.jpg'},
//               {pid: 1003, name: 'ทุเรียนทอด',  icon1: true, icon2: true, icon3: false, title: 'ทุเรียนทอด', avatar: 'pic003.jpg'},
//               {pid: 1004, name: 'ข้าวเกรียบทอด',  icon1: true, icon2: true, icon3: false, title: 'ข้าวเกรียบทอด', avatar: 'pic004.jpg'},
//               {pid: 1005, name: 'กล้วยอบแห้ง',  icon1: true, icon2: true, icon3: true, title: 'กล้วยอบแห้ง', avatar: 'pic005.jpg'},

// ]
      }

  },  

created() {
        console.log('page load')
        this.products.pid = this.$route.query.pid
        this.products.name = this.$route.query.name        
        this.products.detail = this.$route.query.detail
        this.products.price = this.$route.query.price
        this.products.img = this.$route.query.img        
        this.products.star1 = this.$route.query.star1
        this.products.star2 = this.$route.query.star2
        this.products.star3 = this.$route.query.star3
        console.log(this.products.name)        
    },

  methods: {
      doM1() {
        //console.log('aaa')
        console.log(this.$route.query.pid)
        //console.log(this.$route.params.code)

      },
      doM2() {

      },
      doM3() {

      },
      doM4() {

      },
      doM5() {

      }


  }
}
</script>
