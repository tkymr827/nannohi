<template>
  <div id="app">
      <h1>{{content}}</h1>
      <h2>{{month}}月{{day}}日</h2>
      <div class="form">
        <input type="text" v-model="month"><p>月</p>
        <input type="text" v-model="day"><p>日</p>
      </div>

      <button @click="check">見る</button>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'app',
  data () {
    return {
      month: '',
      day: '',
      content: ''
    }
  },
  methods: {
    check: function () {
    //   this.url = 'http://numbersapi.com/' + this.month + '/' + this.day + '/date'
      axios.get('http://numbersapi.com/' + this.month + '/' + this.day + '/date')
        .then(response => {
          this.content = response.data
        })
      axios.get('https://script.google.com/macros/s/AKfycbzoABPxdW3LWsBzO8grBU2O9iqXzYaaza6WmU0Jew3AkL-wtSKG/exec?text=' + this.content + '&source=en&target=jp')
        .then(response => {
          console.log(response)
        })
    }
  }

}
</script>

<style lang="scss">
*{
    padding:0;
    margin:0;
    box-sizing: border-box;
}
html{
    font-size:62.5%;
}
#app {
    background:#3c4c9c ;
    color: #c4b66a;
    min-height:100vh;
    display:flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    .form{
        display:flex;

    }
}

</style>
