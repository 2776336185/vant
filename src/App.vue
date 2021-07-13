<template>
  <div id="app">
  <h2>人员列表</h2>
  <input v-model="keyword" type="text" placeholder="请输入姓名">
  <button @click="sortType = 1">升序</button>
    <button @click="sortType = 2">降序</button>
    <button @click="sortType = 0">原顺序</button>
    <button @click="updata">修改信息</button>
  <li v-for="(p) in fmtpersons" :key="p.id">
    {{p.name}}--{{p.sex}}--{{p.age}}
  </li>
  <van-button type="primary">主要按钮</van-button>
    <router-view />
  </div>
</template>
<script>
export default {
  name: 'App',
  data () {
    return {
      person: [
        { id: '001', name: '马冬梅', age: 35, sex: '女', a: { b: { c: { d: { e: 1 } } } } },
        { id: '002', name: '周冬梅', age: 20, sex: '男' },
        { id: '003', name: '梅', age: 39, sex: '女' },
        { id: '004', name: '冬梅', age: 30, sex: '男' }
      ],
      car: {
        name: '奔驰c63',
        price: '68万',
        color: '灰色'
      },
      n: 3,
      keyword: '',
      sortType: 0// 0原顺序1升序2降序
    }
  },
  methods: {
    updata () {
      this.person[0] = { name: '小佩奇', age: 90, sex: '男' }
      this.person.push()
    }
  },
  // watch: {
  //   keyword (newvalue, oldvalue) {
  //     const arr = this.person.filter(p => p.name.indexOf(newvalue) !== -1)
  //     this.person = arr//使用watch监视元数据会导致原数据的流流失
  //   }
  // }
  computed: {
    fmtpersons () {
      const { person, keyword, sortType } = this
      const arr = person.filter(p => p.name.indexOf(keyword) !== -1)
      if (sortType) {
        arr.sort((a, b) => {
          if (sortType === 1) return a.age - b.age
          else return b.age - a.age
        })
      }
      return arr
    }

  },
  // 实例初始化前
  beforeCreate () {
    // console.log(this)
    // debugger;
  },
  // vue实例初始化完毕
  created () {

  }, // 在此钩子中所有对dom节点的操作都不生效
  // 无法获得解析后的Dom，因为没有mount
  beforeMount () {

  }, // 此钩子中可以操作dom节点此时组件已经脱离了初始化阶段，进入了运行阶段，一般在此阶段开启定时器发送网络请求等准备工作
  mounted () {

  }, // 此钩子中数据是新的但是页面也是新的 即新页面尚未和数据保持同步
  beforeUpdate () {

  },
  // 此钩子中数据是新的页面也是新的页面和数据保持同步
  updated () {

  },
  beforeUnmount () {

  }

}
</script>
<style lang="less">

</style>
