<template>
<div>
          <!-- <ul>
          <li v-for="pd in products" :key="pd.pid">
              {{pd.pid}} {{pd.name}} {{pd.img}}
          </li>
      </ul> -->
  <v-layout row>
    <v-flex xs12 sm6 offset-sm3>
      <v-card>
                  <v-toolbar color="primary">
            <!--v-btn icon-->
              <v-icon color="white">เลือกเพื่อแก้ไขข้อมูลสินค้า</v-icon>
            <!--/v-btn-->
            <v-spacer></v-spacer>
            <v-btn icon>
              <v-icon color="white">more_vert</v-icon>
            </v-btn>
          </v-toolbar>

        <v-list>
          <v-list-tile avatar v-for="(item) in products" :key="item.pid" @click="doM1(item)">
            <v-list-tile-action> 
              <v-icon v-if="item.star1 === 1 && item.star2 === 0 && item.star3 === 0" color="pink">star star_border star_border</v-icon>
              <v-icon v-else-if="item.star1 === 1 && item.star2 === 1 && item.star3 === 0" color="pink">star star star_border</v-icon>
              <v-icon v-else-if="item.star1 === 1 && item.star2 === 1 && item.star3 === 1" color="pink">star star star</v-icon>
            </v-list-tile-action>
            <v-list-tile-content>
              <v-list-tile-title v-text="item.name"></v-list-tile-title>
            </v-list-tile-content>
            <v-list-tile-avatar>
              <img :src="item.img">
            </v-list-tile-avatar>
          </v-list-tile>
        </v-list>
      </v-card>
    </v-flex>
  </v-layout>
  </div>
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
      async created() {
        console.log('page load')
        let res = await this.$http.get('/product')
        console.log(res.data.product)
        this.products = res.data.product


    },
  
  methods: {
    doM1(item){
      //this.$router.push('/otop?pid=' + item.pid + '&name=' + item.name + '&detail=' + item.detail + '&price=' + item.price + '&img=' + item.img + '&star1=' + item.star1 + '&star2=' + item.star2 + '&star3=' + item.star3)
      this.$router.push('/product-edit?pid=' + item.pid)

//this.$router.push('/product/' + item)
      // if (this.items[index].title === 'น้ำพริกกุ้งเสียบ') {
      //   this.$router.push('/_test03?index=' + index)
      // }

    },
    doM2(){

    },
    drawer(){
      
    }

  }
}
</script>
