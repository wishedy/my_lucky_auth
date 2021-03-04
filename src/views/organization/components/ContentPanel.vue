<template>
  <section class="content-panel el-row">
    <section class="content-tree el-col el-col-6  el-col-push-1">
      <section class="handle-content role-handle-content block">
        <h3 class="h-title"> 架构管理 </h3>
        <el-button-group>
          <el-button type="primary" size="mini" icon="el-icon-circle-plus-outline" @click="addRoleGroup">
            新增部门
          </el-button>
          <el-button type="primary" size="mini" icon="el-icon-edit" @click="edit">
            编辑
          </el-button>
          <el-button type="danger" size="mini" icon="el-icon-delete" @click="edit">
            删除
          </el-button>
        </el-button-group>
      </section>
      <el-tree
        :data="list"
        node-key="id"
        default-expand-all
        :expand-on-click-node="false"
      >
        <span slot-scope="{ node }" class="custom-tree-node">
          <span>{{ node.label }}</span>
        </span>
      </el-tree>
    </section>
    <section class="content-form el-col el-col-16 el-col-push-1">
      <section class="handle-content block">
        <h3 class="h-title"> 部门名称 </h3>
        <SearchPanel />
      </section>
      <TablePanel />
    </section>
  </section>
</template>
<script>
import TablePanel from '@/views/organization/components/TablePanel'
import SearchPanel from '@/views/organization/components/SearchPanel'
export default {
  name: 'ContentPanel',
  components: {
    SearchPanel,
    TablePanel
  },
  data() {
    const data = [{
      id: 1,
      label: '部门组1',
      value: 1,
      children: [{
        id: 4,
        label: '部门11',
        value: 1
      }]
    }, {
      id: 2,
      label: '部门组2',
      value: 1,
      children: [{
        id: 5,
        value: 1,
        label: '部门21'
      }, {
        id: 6,
        value: 1,
        label: '部门22'
      }]
    }, {
      id: 3,
      label: '部门组3',
      value: 1,
      children: [{
        id: 7,
        value: 1,
        label: '部门31'
      }, {
        id: 8,
        value: 1,
        label: '部门32'
      }]
    }, {
      id: 22,
      label: '部门组4',
      value: 1,
      children: [{
        id: 9,
        value: 1,
        label: '部门41'
      }, {
        id: 10,
        value: 1,
        label: '部门42'
      }]
    }, {
      id: 11,
      label: '部门组5',
      value: 1,
      children: [{
        id: 7,
        value: 1,
        label: '部门51'
      }, {
        id: 12,
        value: 1,
        label: '部门52'
      }]
    }, {
      id: 13,
      label: '部门组6',
      value: 1,
      children: [{
        id: 7,
        value: 1,
        label: '部门61'
      }, {
        id: 14,
        value: 1,
        label: '部门62'
      }]
    }, {
      id: 15,
      label: '部门组7',
      value: 1,
      children: [{
        id: 16,
        value: 1,
        label: '部门81'
      }, {
        id: 17,
        value: 1,
        label: '部门82'
      }]
    }]
    const menu = [{
      id: 1,
      label: '一级菜单1',
      value: 1,
      children: [{
        id: 4,
        label: '二级菜单11',
        value: 1
      }]
    }, {
      id: 2,
      label: '一级菜单2',
      value: 1,
      children: [{
        id: 5,
        value: 1,
        label: '二级菜单21'
      }, {
        id: 6,
        value: 1,
        label: '二级菜单22'
      }]
    }, {
      id: 3,
      label: '一级菜单3',
      value: 1,
      children: [{
        id: 7,
        value: 1,
        label: '二级菜单31'
      }, {
        id: 8,
        value: 1,
        label: '二级菜单32'
      }]
    }, {
      id: 22,
      label: '一级菜单4',
      value: 1,
      children: [{
        id: 9,
        value: 1,
        label: '二级菜单41'
      }, {
        id: 10,
        value: 1,
        label: '二级菜单42'
      }]
    }, {
      id: 11,
      label: '一级菜单5',
      value: 1,
      children: [{
        id: 7,
        value: 1,
        label: '二级菜单51'
      }, {
        id: 12,
        value: 1,
        label: '二级菜单52'
      }]
    }, {
      id: 13,
      label: '一级菜单6',
      value: 1,
      children: [{
        id: 7,
        value: 1,
        label: '二级菜单61'
      }, {
        id: 14,
        value: 1,
        label: '二级菜单62'
      }]
    }, {
      id: 15,
      label: '一级菜单7',
      value: 1,
      children: [{
        id: 16,
        value: 1,
        label: '二级菜单81'
      }, {
        id: 17,
        value: 1,
        label: '二级菜单82'
      }]
    }]
    return {
      labelPosition: 'right',
      form: {
        show: 1,
        des: '',
        sort: 1,
        name: '',
        icon: '',
        region: '',
        type: ''
      },
      list: JSON.parse(JSON.stringify(data)),
      menuList: JSON.parse(JSON.stringify(menu))
    }
  },
  methods: {
    addRoleGroup() {
      console.log('点击')
      this.$emit('handleAddRoleGroup')
    },
    addRole() {
      this.$emit('handleAddRole')
    },
    edit() {
      this.$emit('handleEdit')
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
.content-form,.content-tree{
  max-height: 800px;
  min-height: 600px;
  padding: 20px;
  box-shadow: rgb(230, 230, 230) 10px 10px 30px 5px;
  .handle-content{
    padding-bottom: 20px;
  }
  .role-handle-content{
    padding-bottom: 70px;
  }
}
</style>
