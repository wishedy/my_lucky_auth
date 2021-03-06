<template>
  <section class="handle-wrap">
    <el-button-group>
      <el-button type="primary" @click="handleLeave">
        离职
      </el-button>
    </el-button-group>
    <el-popover placement="top-start" title="温馨提示" width="200" trigger="hover">
      <li>离职操作不可逆请确认完毕后再进行操作</li>
      <el-button slot="reference" size="mini" icon="el-icon-info" style="float:right">
        操作提示
      </el-button>
    </el-popover>
  </section>
</template>
<script>
export default {
  name: 'HandleBar',
  methods: {
    handleLeave () {
      const _this = this
      _this.$confirm('员工离职后，员工将无法登陆相关系统，是否确定离职？', '确认信息', {
        distinguishCancelAndClose: true,
        confirmButtonText: '保存',
        cancelButtonText: '放弃修改'
      })
        .then(() => {
          this.$message({
            type: 'info',
            message: '保存修改'
          })
        })
        .catch(action => {
          this.$message({
            type: 'info',
            message: action === 'cancel'
              ? '放弃保存并离开页面'
              : '停留在当前页面'
          })
        })
    }
  }
}
</script>
