<template>
  <div class="home">
    <vue-qr v-if="qr" :text="qr" :size="200"></vue-qr>
    <button @click="getqr()">click</button>
  </div>
</template>

<script>
import VueQr from 'vue-qr'
import axios from 'axios'

export default {
  name: 'Home',
  data() {
      return {
          qr: null
      }
  },
  methods: {
      getqr () {
          axios
            .get('http://192.168.1.10:3200/qr', {})
            .then(response => {
                this.qr = response.data
            })
      }
  }, 
  components: {
      VueQr
  }
}
</script>
