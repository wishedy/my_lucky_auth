<template>
  <section class="el-main">
    <ContentPanel @handleAddRoleGroup="editGroup" @handleAddRole="editRole" @handleEdit="editRole" />
    <EditGroupPanel :visible.sync="visible" @handleCancel="closeEdit" />
    <EditRolePanel :visible.sync="roleVisible" @handleCancel="closeRoleEdit" />
  </section>
</template>
<script>
import ContentPanel from '@/views/user-roles/components/ContentPanel'
import EditGroupPanel from '@/views/user-roles/components/EditGroupPanel'
import EditRolePanel from '@/views/user-roles/components/EditRolePanel'
export default {
  name: 'Administrator',
  components: {
    EditGroupPanel,
    EditRolePanel,
    ContentPanel
  },
  data() {
    return {
      visible: false,
      roleVisible: false
    }
  },
  methods: {
    editGroup() {
      this.visible = true
    },
    editRole() {
      this.roleVisible = true
    },
    closeEdit() {
      console.log('触发')
      this.visible = false
    },
    closeRoleEdit() {
      console.log('触发')
      this.roleVisible = false
    },
    editData() {
      this.visible = true
    }
  }
}
</script>
