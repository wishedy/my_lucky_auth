<template>
  <BaseDrawer
    :visible="visible"
    :show-footer="false"
    title="编辑角色权限"
    width="770px"
    @confirm="handleConfirm"
    @cancel="$emit('handleCancel')"
    @close="$emit('handleCancel')"
  >
    <Authority />
  </BaseDrawer>
</template>
<script>
import BaseDrawer from '@/components/Drawer/BaseDrawer'
import Authority from '@/components/Authority/Authority'
export default {
  name: 'EditPanel',
  components: {
    BaseDrawer,
    Authority
  },
  props: {
    visible: {
      type: Boolean,
      default: false
    }
  },
  methods: {
    handleConfirm () {
      console.log('点击确定')
    }
  }
}
</script>
