<template>
  <section class="el-main">
    <SearchPanel />
    <TablePanel @handleEdit="editData" />
    <EditPanel :visible.sync="visible" @handleCancel="closeEdit" />
  </section>
</template>
<script>
import EditPanel from '@/views/journal/components/EditPanel'
import SearchPanel from '@/views/journal/components/SearchPanel'
import TablePanel from '@/views/journal/components/TablePanel'
export default {
  name: 'Journal',
  components: {
    SearchPanel,
    TablePanel,
    EditPanel
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
