<template>
  <BaseDrawer
    :visible="visible"
    :show-footer="true"
    title="新增部门"
    width="500px"
    @confirm="handleConfirm"
    @cancel="$emit('handleCancel')"
    @close="$emit('handleCancel')"
  >
    <el-form :label-position="labelPosition" label-width="100px" :model="form" :rules="rules">
      <el-form-item label="部门名称" prop="name">
        <el-input v-model="form.name" placeholder="请输入部门名称，最大10个字符，不可重复" />
      </el-form-item>
    </el-form>
  </BaseDrawer>
</template>
<script>
import BaseDrawer from '@/components/Drawer/BaseDrawer'
export default {
  name: 'EditPanel',
  components: {
    BaseDrawer
  },
  props: {
    visible: {
      type: Boolean,
      default: false
    }
  },
  data () {
    return {
      labelPosition: 'right',
      rules: {
        name: [
          {
            required: true,
            message: '部门名称不能为空',
            trigger: 'blur'
          }
        ]
      },
      form: {
        name: ''
      }
    }
  },
  methods: {
    handleConfirm () {
      console.log('点击确定')
    }
  }
}
</script>
