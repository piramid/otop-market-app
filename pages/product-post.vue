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
          <v-checkbox label="ติดดาว 1 ดวง" v-model="checkbox1" @click="cb1"></v-checkbox>
          <v-checkbox label="ติดดาว 2 ดวง" v-model="checkbox2" @click="cb2"></v-checkbox>
          <v-checkbox label="ติดดาว 3 ดวง" v-model="checkbox3" @click="cb3"></v-checkbox>

</v-flex>

              <!-- <v-flex xs12>
                <v-text-field
                  :rules="[(v) => v.length <= 50 || 'Max 50 characters']"
                  :counter="50"
                  v-model="star1"
                  label="ดาว 1"
                ></v-text-field>
              <v-checkbox :label="`ดาว 1 ดวง: ${checkbox1.toString()}`" v-model="checkbox1"></v-checkbox>

              </v-flex>

              <v-flex xs12>
                <v-text-field
                  :rules="[(v) => v.length <= 50 || 'Max 50 characters']"
                  :counter="50"
                  v-model="star2"
                  label="ดาว 2"
                ></v-text-field>
              <v-checkbox :label="`ดาว 2 ดวง: ${checkbox2.toString()}`" v-model="checkbox2"></v-checkbox>
              </v-flex>

              <v-flex xs12>
                <v-text-field
                  :rules="[(v) => v.length <= 50 || 'Max 50 characters']"
                  :counter="50"
                  v-model="star3"
                  label="ดาว 3"
                ></v-text-field>
              <v-checkbox :label="`ดาว 3 ดวง: ${checkbox3.toString()}`" v-model="checkbox3"></v-checkbox>
              </v-flex>               -->





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
        checkbox1: false,
        checkbox2: false,
        checkbox3: false,
        chk1: 0,
        chk2: 0,
        chk3: 0,

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
 
    created() {
        console.log(this.checkbox1.toString())

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
                star1: this.chk1,
                star2: this.chk2,
                star3: this.chk3,
            })
             

            if (!res.data.ok) {
                ///
                this.$router.push('/product-list')
            } else {
                ///
            }
            
        },

        cb1() {
            this.checkbox1 = !this.checkbox1
            console.log(this.checkbox1.toString())
            if (this.checkbox1 == true) {
              console.log("OK")
              this.chk1 = 1
            } else {
              this.chk1 = 0
            }
            console.log(this.chk1)
        },
        cb2() {
            this.checkbox2 = !this.checkbox2
            console.log(this.checkbox2.toString())
            if (this.checkbox1 == true) {
              this.chk2 = 1
            } else {
              this.chk2 = 0
            }
            console.log(this.chk2)
        },
        cb3() {
            this.checkbox3 = !this.checkbox3
            console.log(this.checkbox3.toString())
            if (this.checkbox1 == true) {
              this.chk3 = 1
            } else {
              this.chk3 = 0
            }
            console.log(this.chk3)
        }



    },
  }
</script>