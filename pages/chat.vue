<template>
  <div>
      <h1>Chat Room</h1>
      <div>
          <v-text-field v-model="name" label="ชื่อสินค้า"></v-text-field>
                <v-text-field v-model="text" label="ข้อความ"></v-text-field>
                    <v-btn @click="send">ส่ง</v-btn>    
      </div>
      <ul>
          <li v-for="(m, index) in msg" :key="index">
              <b>{{m.name}}</b> พูดว่า {{m.text}}
          </li>
      </ul>

  </div>
</template>

<script>
export default {
  data() {
    return {
      name: '',
      text: '',
      msg: []
    };
  },

  created() {
    this.$socket.subscribe('room39', this.onMsg)
  },

  beforeDestroy() {
    this.$socket.unsubscribe('room39')
  },

  methods: {
    send() {
        this.$socket.publish('room39', {
            name: this.name,
            text: this.text,
        })
    },

    onMsg(data) {
        console.log(data)
        //this.msg.push(data)
        this.msg.unshift(data)
    }
    
  }
};
</script>

