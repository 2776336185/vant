<template>
  <div id="app">
    <h1>axios的使用</h1>
    <button @click="getReq()">发起get请求</button>
    <router-view />
  </div>
</template>
<script>
import axios from 'axios'
export default {
  setup () {
    const getReq = () => {
      axios
        .get(
          'http://demo.itlike.com/web/xlmc/api/homeApi/categoriesdateil/lk001'
        )
        .then((res) => {
          console.log(res.data)
        })
        .catch((error) => {
          console.log(error)
        })
    }
    return {
      getReq
    }
  }
}
</script>
<style lang="less">
</style>
