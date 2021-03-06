<template>
  <section class="el-main">
    <SearchPanel />
    <HandleBar />
    <TablePanel @handleEdit="editData" />
    <EditPanel :visible.sync="visible" @handleCancel="closeEdit" />
  </section>
</template>
<script>
import EditPanel from '@/views/administrator/components/EditPanel'
import SearchPanel from '@/views/administrator/components/SearchPanel'
import TablePanel from '@/views/administrator/components/TablePanel'
import HandleBar from '@/views/administrator/components/HandleBar'
export default {
  name: 'Administrator',
  components: {
    SearchPanel,
    TablePanel,
    EditPanel,
    HandleBar
  },
  data () {
    return {
      visible: false
    }
  },
  methods: {
    closeEdit () {
      console.log('触发')
      this.visible = false
    },
    editData () {
      this.visible = true
    }
  }
}
</script>
