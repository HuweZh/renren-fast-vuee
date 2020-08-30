<template>
  <el-tree :data="menus" :props="defaultProps" @node-click="handleNodeClick"></el-tree>
</template>

<script>
  export default {
    name: 'category',
    data () {
      return {
        menus: [],
        defaultProps: {
          // 子节点
          children: 'children',
          // 要显示的内容
          label: 'name'
        }
      }
    },
    methods: {
      handleNodeClick (data) {
        console.log(data)
      },
      // 获取所有菜单
      getMenus () {
        this.$http({
          url: this.$http.adornUrl('/gulimallproduct/category/list/tree'),
          method: 'get'
        }).then((data) => {  // 解构出data的数据
          this.menus = data.data.data
          //console.log(this.menus)
        })
      }
    },
    created () {
      this.getMenus()
    }
  }
</script>

<style scoped>

</style>
