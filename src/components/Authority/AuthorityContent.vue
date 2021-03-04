<template>
  <section class="authority-content">
    <div class="custom-tree-container">
      <div class="block">
        <el-tree
          :data="list"
          show-checkbox
          node-key="id"
          default-expand-all
          :expand-on-click-node="false"
        >
          <span slot-scope="{ node }" class="custom-tree-node">
            <span>{{ node.label }}</span>
            <span class="handle-tree">
              <el-tooltip :content="'Switch value: ' + node.value" placement="top">
                <el-switch
                  v-model="node.value"
                  active-color="#13ce66"
                  inactive-color="#dcdfe6"
                  active-value="100"
                  inactive-value="0"
                />
              </el-tooltip>
              <!--              <el-button
                type="text"
                size="mini"
                @click="() => append(data)"
              >
                Append
              </el-button>
              <el-button
                type="text"
                size="mini"
                @click="() => remove(node, data)"
              >
                Delete
              </el-button>-->
            </span>
          </span>
        </el-tree>
      </div>
    </div>
  </section>
</template>
<script>
export default {
  name: 'AuthorityContent',
  data() {
    const data = [{
      id: 1,
      label: '一级菜单-1',
      value: 1,
      children: [{
        id: 4,
        label: '二级菜单-1',
        value: 1,
        children: [{
          id: 9,
          value: 1,
          label: '三级菜单-1'
        }, {
          id: 10,
          value: 1,
          label: '三级菜单-2'
        }]
      }]
    }, {
      id: 2,
      label: '一级菜单-2',
      value: 1,
      children: [{
        id: 5,
        value: 1,
        label: '二级菜单2-1'
      }, {
        id: 6,
        value: 1,
        label: '二级菜单2-2'
      }]
    }, {
      id: 3,
      label: '一级菜单-3',
      value: 1,
      children: [{
        id: 7,
        value: 1,
        label: '二级菜单3-1'
      }, {
        id: 8,
        value: 1,
        label: '二级菜单3-2'
      }]
    }]
    return {
      value: 1111,
      list: JSON.parse(JSON.stringify(data))
    }
  },
  methods: {
    append(data) {
      console.log(data)
      /* const newChild = { id: id++, label: 'testtest', children: [] }
      if (!data.children) {
        this.$set(data, 'children', [])
      }
      data.children.push(newChild)*/
    },

    remove(node, data) {
      const parent = node.parent
      const children = parent.data.children || parent.data
      const index = children.findIndex(d => d.id === data.id)
      children.splice(index, 1)
    }
  }
}
</script>
<style lang="scss" scoped>
.custom-tree-node{
  flex: 1;
  display: flex;
  align-items: center;
  justify-content: space-between;
  font-size: 14px;
  padding-right: 8px;
}
.handle-tree{
  float: right;
}
</style>
