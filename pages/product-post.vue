<template>
  <v-container fluid grid-list-xl>
    <v-layout row wrap>
      <v-flex xs12 class="my-3">
        <v-card>
          <v-toolbar color="primary">
            <!--v-btn icon-->
              <v-icon color="white">เพิ่มข้อมูลสินค้า</v-icon>
            <!--/v-btn-->
            <v-spacer></v-spacer>
            <v-btn icon>
              <v-icon color="white">more_vert</v-icon>
            </v-btn>
          </v-toolbar>
          <v-container fluid class="px-3">
            <v-layout row wrap>

              <v-flex xs12>
                <v-text-field
                  :rules="[(v) => v.length <= 4 || 'Max 4 characters']"
                  :counter="4"
                  v-model="pid"
                  label="รหัสสินค้า"
                ></v-text-field>
              </v-flex>

              <v-flex xs12>
                <v-text-field
                  :rules="[(v) => v.length <= 50 || 'Max 50 characters']"
                  :counter="50"
                  v-model="name"
                  label="ชื่อสินค้า"
                ></v-text-field>
              </v-flex>

              <v-flex xs12>
                <v-text-field
                  :rules="[(v) => v.length <= 50 || 'Max 50 characters']"
                  :counter="50"
                  v-model="detail"
                  label="รายละเอียด"
                ></v-text-field>
              </v-flex>

              <v-flex xs12>
                <v-text-field
                  :rules="[(v) => v.length <= 50 || 'Max 50 characters']"
                  :counter="50"
                  v-model="price"
                  label="ราคา"
                ></v-text-field>
              </v-flex>

              <v-flex xs12>
                <v-text-field
                  :rules="[(v) => v.length <= 50 || 'Max 50 characters']"
                  :counter="50"
                  v-model="img"
                  label="รูปภาพ"
                ></v-text-field>
              </v-flex>

              <v-flex xs12>
                <v-text-field
                  :rules="[(v) => v.length <= 50 || 'Max 50 characters']"
                  :counter="50"
                  v-model="star1"
                  label="ดาว 1"
                ></v-text-field>
              </v-flex>

              <v-flex xs12>
                <v-text-field
                  :rules="[(v) => v.length <= 50 || 'Max 50 characters']"
                  :counter="50"
                  v-model="star2"
                  label="ดาว 2"
                ></v-text-field>
              </v-flex>

              <v-flex xs12>
                <v-text-field
                  :rules="[(v) => v.length <= 50 || 'Max 50 characters']"
                  :counter="50"
                  v-model="star3"
                  label="ดาว 3"
                ></v-text-field>
              </v-flex>              





            </v-layout>
          </v-container>

          <v-toolbar color="primary">

    <v-btn color="success" @click="post">Save</v-btn>
    <v-btn color="error">Cancel</v-btn>

          </v-toolbar>


        </v-card>
      </v-flex>
    </v-layout>
  </v-container>
</template>

<script>
  export default {
    data () {
      return {
        pid: '',
        name: '',
        detail: '',
        price: '',
        img: '',
        star1: '',
        star2: '',
        star3: '',
      }
    },
    methods: {
        async post() {

             console.log(this.pid)
             console.log(this.name)
             console.log(this.detail)

            let res = await this.$http.post('/product/add', {
                pid: this.pid,
                name: this.name,
                detail: this.detail,
                price: this.price,
                img: this.img,
                star1: this.star1,
                star2: this.star2,
                star3: this.star3,
            })
             

            if (!res.data.ok) {
                ///
            } else {
                ///
            }
            
        },


    },
  }
</script>