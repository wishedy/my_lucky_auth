<template>
  <section class="search-wrap">
    <el-form
      ref="searchForm"
      :model="formData"
      :inline="true"
      label-width="110px"
    >
      <el-form-item
        label="ID:"
        prop="search"
      >
        <el-input
          v-model="formData.title"
          class="search-box"
          type="text"
          placeholder="请输入员工ID"
          @keyup.enter.native="handleSearch"
        />
      </el-form-item>
      <el-form-item
        label="姓名:"
        prop="search"
      >
        <el-input
          v-model="formData.title"
          class="search-box"
          type="text"
          placeholder="请输入姓名"
          @keyup.enter.native="handleSearch"
        />
      </el-form-item>
      <el-form-item
        label="邮箱:"
        prop="search"
      >
        <el-input
          v-model="formData.title"
          class="search-box"
          type="text"
          placeholder="请输入邮箱"
          @keyup.enter.native="handleSearch"
        />
      </el-form-item>
      <el-form-item
        label="手机号:"
        prop="search"
      >
        <el-input
          v-model="formData.title"
          class="search-box"
          type="text"
          placeholder="请输入手机号"
          @keyup.enter.native="handleSearch"
        />
      </el-form-item>
      <el-form-item
        label="状态:"
        prop="status"
      >
        <el-select v-model="formData.status" clearable placeholder="请选择管理员状态" class="search-box">
          <el-option
            v-for="item in status"
            :key="item.id"
            :label="item.name"
            :value="item.id"
          />
        </el-select>
      </el-form-item>
      <el-form-item class="form-button-line block">
        <el-button
          type="primary"
          icon="el-icon-search"
          @click="handleSearch"
        >查询</el-button>
        <el-button
          type="warning"
          icon="el-icon-refresh"
          @click="handleReset"
        >重置</el-button>
      </el-form-item>
    </el-form>
  </section>
</template>
<script>
export default {
  name: 'AdminSearch',
  data() {
    return {
      status: [
        {
          id: 0,
          name: '离职'
        },
        {
          id: 1,
          name: '在职'
        }
      ],
      roles: [{
        id: 0,
        name: '暂无角色'
      }, {
        id: 1,
        name: '超级管理员'
      }, {
        id: 2,
        name: '普通管理员'
      }, {
        id: 3,
        name: '小编'
      }],
      originalForm: {
        status: '',
        role: '',
        title: ''
      },
      formData: {
        status: '',
        role: '',
        title: ''
      }
    }
  },
  methods: {
    handleSearch() {
      this.$emit('search', this.formData)
    },
    handleReset() {
      const _this = this
      _this.formData = JSON.parse(JSON.stringify(_this.originalForm))
      console.log(_this.formData)
      console.log('重置参数')
      _this.$emit('search', _this.formData)
    },
    handleCreate() {
      this.$emit('create')
    }
  }
}
</script>
