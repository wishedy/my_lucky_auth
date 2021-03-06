<template>
  <section class="table-wrap">
    <el-table
      :data="list"
      border
    >
      <el-table-column prop="id" label="操作ID" />
      <el-table-column prop="user_id" label="操作人ID" />
      <el-table-column prop="user_name" label="操作人姓名" />
      <el-table-column prop="handleId" label="被操作人ID" />
      <el-table-column prop="handle_user_name" label="被操作人姓名" />
      <el-table-column prop="action_type" label="修改类型" />
      <el-table-column prop="action_log" label="修改日志">
        <template slot-scope="scope">
          <article style="color:#ff0000;" v-text="scope.row.action_log" />
        </template>
      </el-table-column>
      <el-table-column prop="time" label="修改时间" />
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
        id: '444444411',
        handleId: '1212431',
        user_id: '88888888',
        link: '111',
        email: 'webheng@126.com',
        user_name: '张恒',
        handle_user_name: '赵双全',
        action_type: '角色',
        action_log: '角色有修改\n' +
          '旧角色为：无\n' +
          '新角色为： 超级管理员, 老师, 外管, 班管, 教学研发, 美标CC, TMK, CC主管, 外教招聘, EDU系统, 增长, OA, EDU研发, 欧标CC',
        roles_name: '超级管理员、薪酬、运营、研发',
        time: '2019-02-02 19:00',
        image_url: '11111',
        status: 0
      }, {
        id: '4341321',
        handleId: '545454',
        user_id: '09098',
        link: '111',
        email: 'webheng@126.com',
        user_name: '张恒',
        handle_user_name: '赵双全',
        action_type: '路由',
        action_log: '路由有修改\n' +
          '原路由：无\n' +
          '新路由为：菜单名称-权限标识-路由名称router',
        roles_name: '超级管理员、薪酬、运营、研发',
        time: '2019-02-02 19:00',
        image_url: '11111',
        status: 0
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
