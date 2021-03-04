<template>
  <section class="authority">
    <section class="handle-title">
      <span class="edit-title" style="margin-right: 20px;">角色名称</span>
      <el-button type="primary" style="display: inline-block;">保存权限</el-button>
      <el-popover placement="top-start" title="温馨提示" width="200" trigger="hover">
        <li>只针对相应的角色进行权限修改</li>
        <li>修改后记得点击保存权限</li>
        <el-button slot="reference" size="mini" icon="el-icon-info" style="float:right">
          操作提示
        </el-button>
      </el-popover>
    </section>
    <el-tabs type="border-card" class="content">
      <el-tab-pane>
        <span slot="label"><i class="el-icon-date" />crm系统</span>
        <AuthorityContent />
      </el-tab-pane>
      <el-tab-pane label="MOP系统">
        <AuthorityContent />
      </el-tab-pane>
      <el-tab-pane label="auth系统">
        <AuthorityContent />
      </el-tab-pane>
      <el-tab-pane label="HR系统">
        <AuthorityContent />
      </el-tab-pane>
    </el-tabs>
  </section>
</template>
<script>
import AuthorityContent from '@/components/Authority/AuthorityContent'
export default {
  name: 'Authority',
  components: {
    AuthorityContent
  }
}
</script>
<style lang="scss" scoped>
.content{
  height: 70vh;
}
</style>
