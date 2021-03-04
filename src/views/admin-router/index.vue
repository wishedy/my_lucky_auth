<template>
  <section class="el-main">
    <ContentPanel />
    <EditPanel :visible.sync="visible" @handleCancel="closeEdit" />
  </section>
</template>
<script>
import ContentPanel from '@/views/admin-router/components/ContentPanel'
import EditPanel from '@/views/administrator/components/EditPanel'
export default {
  name: 'Administrator',
  components: {
    EditPanel,
    ContentPanel
  },
  data() {
    return {
      visible: false
    }
  },
  methods: {
    closeEdit() {
      console.log('触发')
      this.visible = false
    }
  }
}
</script>
