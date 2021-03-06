<template>
  <section class="el-main">
    <ContentPanel @handleAddRoleGroup="editGroup" />
    <EditGroupPanel :visible.sync="visible" @handleCancel="closeEdit" />
  </section>
</template>
<script>
import EditGroupPanel from '@/views/organization/components/EditGroupPanel'
import ContentPanel from '@/views/organization/components/ContentPanel'
export default {
  name: 'Organization',
  components: {
    ContentPanel,
    EditGroupPanel
  },
  data () {
    return {
      visible: false
    }
  },
  methods: {
    editGroup () {
      this.visible = true
    },
    closeEdit () {
      console.log('触发')
      this.visible = false
    }
  }
}
</script>
