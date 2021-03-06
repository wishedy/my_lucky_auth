<template>
  <section class="table-wrap">
    <el-table
      :data="list"
      border
    >
      <el-table-column width="70" prop="id" label="ID" />
      <el-table-column prop="user_name" label="管理员名称" />
      <el-table-column prop="email" label="邮箱" />
      <el-table-column prop="phone_number" label="手机号" />
      <el-table-column prop="roles_name" label="角色" />
      <el-table-column prop="department" label="部门" />
      <el-table-column prop="time" label="入职时间" />
      <el-table-column prop="status_name" label="状态">
        <template slot-scope="scope">
          <el-tag
            v-if="parseInt(scope.row.status,10)===0"
            type="danger"
            effect="dark"
          >
            离职
          </el-tag>
          <el-tag
            v-if="parseInt(scope.row.status,10)===1"
            type="success"
            effect="dark"
          >
            在职
          </el-tag>
        </template>
      </el-table-column>
      <el-table-column label="操作" fixed="right" align="center">
        <template slot-scope="scope">
          <el-button v-if="parseInt(scope.row.status,10)===0" size="mini" icon="el-icon-edit" circle title="编辑" type="primary" @click="$emit('handleEdit',scope.row)" />
          <el-button v-if="parseInt(scope.row.status,10)===0" type="danger" title="删除" size="mini" icon="el-icon-delete" circle />
          <el-button v-if="parseInt(scope.row.status,10)===1" type="warning" title="用户列表" size="mini" icon="el-icon-share" circle />
          <el-button v-if="parseInt(scope.row.status,10)===1" title="权限" size="mini" icon="el-icon-setting" circle />
        </template>
      </el-table-column>
    </el-table>
    <!-- 分页 -->
    <div class="page">
      <el-pagination
        :current-page="page"
        :page-sizes="[10, 20, 30, 50]"
        :page-size="pageSize"
        layout="total, sizes, prev, pager, next, jumper"
        :total="total"
        @size-change="handleSizeChange"
        @current-change="handleCurrentChange"
      />
    </div>
  </section>
</template>
<script>
export default {
  name: 'AdminTable',
  data () {
    return {
      page: 1,
      pageSize: 20,
      total: 400,
      list: [{
        id: '11111111',
        link: '111',
        email: 'webheng@126.com',
        user_name: '张恒',
        department: '增长前端',
        roles_name: '超级管理员、薪酬、运营、研发',
        time: '2019-02-02 19:00',
        image_url: '11111',
        status: 0
      }, {
        link: '111',
        image_url: '11111',
        status: 1
      }]
    }
  },
  methods: {
    handleSizeChange (size) {
      console.log(size)
    },
    handleCurrentChange (page) {
      console.log(page)
    }
  }
}
</script>
<style lang="scss" scoped>
.table-wrap{

}
</style>
