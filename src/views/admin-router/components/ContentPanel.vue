<template>
  <section class="content-panel el-row">
    <section class="content-tree el-col el-col-10  el-col-push-1">
      <section class="handle-content block">
        <h3 class="h-title"> 路由管理 </h3>
        <el-button-group>
          <el-button type="primary" size="mini" icon="el-icon-circle-plus-outline">
            添加
          </el-button>
          <el-button type="primary" size="mini" icon="el-icon-edit">
            编辑
          </el-button>
          <el-button type="primary" size="mini" icon="el-icon-delete">
            删除
          </el-button>
          <el-button type="primary" size="mini">
            取消
          </el-button>
        </el-button-group>
        <el-popover placement="top-start" title="温馨提示" width="200" trigger="hover">
          <li>添加前需要选择要添加的目录</li>
          <li>请确认完之后再做删除</li>
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
      <el-form :label-position="labelPosition" label-width="80px" :model="form">
        <el-form-item label="父级节点">
          <el-input v-model="form.name" />
        </el-form-item>
        <el-form-item label="路由name">
          <el-input v-model="form.region" />
        </el-form-item>
        <el-form-item label="标题">
          <el-input v-model="form.type" />
        </el-form-item>
        <el-form-item label="菜单描述">
          <el-input v-model="form.des" />
        </el-form-item>
        <el-form-item label="路由路径">
          <el-input v-model="form.type" />
        </el-form-item>
        <el-form-item label="图标">
          <select-icon
            v-model="form.icon"
            :user-input="true"
          />
        </el-form-item>
        <el-form-item label="权限标识">
          <el-input v-model="form.type" />
        </el-form-item>
        <el-form-item label="显示菜单">
          <el-tooltip :content="'Switch value: ' + form.show" placement="top">
            <el-switch
              v-model="form.show"
              active-color="#13ce66"
              inactive-color="#dcdfe6"
              active-value="100"
              inactive-value="0"
            />
          </el-tooltip>
        </el-form-item>
        <el-form-item label="排序">
          <el-input-number v-model="form.sort" :min="1" />
        </el-form-item>
      </el-form>
    </section>
  </section>
</template>
<script>
import SelectIcon from '@/components/SelectIcon/SelectIcon'
export default {
  name: 'ContentPanel',
  components: {
    SelectIcon
  },
  data() {
    const data = [{
      id: 1,
      label: 'MOP系统',
      value: 1,
      children: [{
        id: 4,
        label: '一级菜单-1',
        value: 1,
        children: [{
          id: 9,
          value: 1,
          label: '二级菜单-1'
        }, {
          id: 10,
          value: 1,
          label: '二级菜单-2'
        }]
      }]
    }, {
      id: 2,
      label: 'CRM系统',
      value: 1,
      children: [{
        id: 5,
        value: 1,
        label: '一级菜单2-1',
        children: [{
          id: 9,
          value: 1,
          label: '二级菜单2-1'
        }, {
          id: 10,
          value: 1,
          label: '二级菜单2-2'
        }]
      }, {
        id: 6,
        value: 1,
        label: '一级菜单2-2',
        children: [{
          id: 9,
          value: 1,
          label: '二级菜单2-2-1'
        }, {
          id: 10,
          value: 1,
          label: '二级菜单2-2-2'
        }]
      }]
    }, {
      id: 3,
      label: 'AUTH系统',
      value: 1,
      children: [{
        id: 7,
        value: 1,
        label: '一级菜单3-1'
      }, {
        id: 8,
        value: 1,
        label: '一级菜单3-2'
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
      list: JSON.parse(JSON.stringify(data))
    }
  }
}
</script>
<style lang="scss" scoped>
.content-tree{
  max-height: 800px;
  min-height: 600px;
  padding: 20px;
  box-shadow: rgb(230, 230, 230) 10px 10px 30px 5px;
  .handle-content{
    padding-bottom: 20px;
  }
}
.content-form{
  max-height: 800px;
  min-height: 600px;
  padding: 20px;
}
</style>
