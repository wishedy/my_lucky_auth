<template>
  <section class="content-panel el-row">
    <section class="content-tree el-col el-col-12  el-col-push-1">
      <section class="handle-content role-handle-content block">
        <h3 class="h-title"> 角色管理 </h3>
        <el-button-group>
          <el-button type="primary" size="mini" icon="el-icon-circle-plus-outline" @click="addRoleGroup">
            新增角色组
          </el-button>
          <el-button type="primary" size="mini" icon="el-icon-delete" @click="addRole">
            新增角色
          </el-button>
          <el-button type="primary" size="mini" icon="el-icon-edit" @click="edit">
            编辑
          </el-button>
        </el-button-group>
        <el-popover placement="top-start" title="温馨提示" width="200" trigger="hover">
          <li>离职操作不可逆请确认完毕后再进行操作</li>
          <el-button slot="reference" size="mini" icon="el-icon-info" style="float:right">
            操作提示
          </el-button>
        </el-popover>
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
    <section class="content-form el-col el-col-10 el-col-push-1">
      <section class="handle-content block">
        <h3 class="h-title"> 角色名称 </h3>
        <el-button-group>
          <el-button type="primary" size="mini">
            保存权限
          </el-button>
        </el-button-group>
        <el-popover placement="top-start" title="温馨提示" width="200" trigger="hover">
          <li>离职操作不可逆请确认完毕后再进行操作</li>
          <el-button slot="reference" size="mini" icon="el-icon-info" style="float:right">
            操作提示
          </el-button>
        </el-popover>
      </section>
      <el-tabs class="content">
        <el-tab-pane>
          <span slot="label"><i class="el-icon-date" />crm系统</span>
          <el-tree
            :data="menuList"
            node-key="id"
            default-expand-all
            style="background: none;"
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
              </span>
            </span></el-tree>
        </el-tab-pane>
        <el-tab-pane label="MOP系统" />
        <el-tab-pane label="auth系统" />
        <el-tab-pane label="HR系统" />
      </el-tabs>

    </section>
  </section>
</template>
<script>
export default {
  name: 'ContentPanel',
  data() {
    const data = [{
      id: 1,
      label: '角色组1',
      value: 1,
      children: [{
        id: 4,
        label: '角色11',
        value: 1
      }]
    }, {
      id: 2,
      label: '角色组2',
      value: 1,
      children: [{
        id: 5,
        value: 1,
        label: '角色21'
      }, {
        id: 6,
        value: 1,
        label: '角色22'
      }]
    }, {
      id: 3,
      label: '角色组3',
      value: 1,
      children: [{
        id: 7,
        value: 1,
        label: '角色31'
      }, {
        id: 8,
        value: 1,
        label: '角色32'
      }]
    }, {
      id: 22,
      label: '角色组4',
      value: 1,
      children: [{
        id: 9,
        value: 1,
        label: '角色41'
      }, {
        id: 10,
        value: 1,
        label: '角色42'
      }]
    }, {
      id: 11,
      label: '角色组5',
      value: 1,
      children: [{
        id: 7,
        value: 1,
        label: '角色51'
      }, {
        id: 12,
        value: 1,
        label: '角色52'
      }]
    }, {
      id: 13,
      label: '角色组6',
      value: 1,
      children: [{
        id: 7,
        value: 1,
        label: '角色61'
      }, {
        id: 14,
        value: 1,
        label: '角色62'
      }]
    }, {
      id: 15,
      label: '角色组7',
      value: 1,
      children: [{
        id: 16,
        value: 1,
        label: '角色81'
      }, {
        id: 17,
        value: 1,
        label: '角色82'
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
