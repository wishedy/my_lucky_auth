<template>
  <BaseDrawer
    :visible="visible"
    :show-footer="true"
    title="新增角色"
    width="500px"
    @confirm="handleConfirm"
    @cancel="$emit('handleCancel')"
    @close="$emit('handleCancel')"
  >
    <el-form :label-position="labelPosition" label-width="100px" :model="form" :rules="rules">
      <el-form-item label="角色名称" prop="name">
        <el-input v-model="form.name" placeholder="请输入角色名称，最大10个字符，不可重复" />
      </el-form-item>
      <el-form-item label="角色组" prop="region">
        <el-select v-model="form.region" placeholder="请选择角色组">
          <el-option label="角色组1" value="shanghai" />
          <el-option label="角色组2" value="beijing" />
        </el-select>
      </el-form-item>
    </el-form>
  </BaseDrawer>
</template>
<script>
import BaseDrawer from '@/components/Drawer/BaseDrawer'
export default {
  name: 'EditRolePanel',
  components: {
    BaseDrawer
  },
  props: {
    visible: {
      type: Boolean,
      default: false
    }
  },
  data() {
    return {
      labelPosition: 'right',
      rules: {
        name: [
          {
            required: true,
            message: '角色名称不能为空',
            trigger: 'blur'
          }
        ],
        region: [
          {
            required: true,
            message: '角色组名称不能为空',
            trigger: 'blur'
          }
        ]
      },
      form: {
        name: '',
        region: ''
      }
    }
  },
  methods: {
    handleConfirm() {
      console.log('点击确定')
    }
  }
}
</script>
