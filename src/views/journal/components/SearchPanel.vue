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
          placeholder="请输入操作人ID"
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
          placeholder="请输入操作人姓名"
          @keyup.enter.native="handleSearch"
        />
      </el-form-item>
      <el-form-item
        label="修改类型:"
        prop="status"
      >
        <el-select v-model="formData.role" clearable placeholder="请选择操作类型" class="search-box">
          <el-option
            v-for="item in roles"
            :key="item.id"
            :label="item.name"
            :value="item.id"
          />
        </el-select>
      </el-form-item>
      <el-form-item
        label="日期:"
        prop="search"
      >
        <el-date-picker
          v-model="date"
          type="date"
          :picker-options="pickerOptions"
          placeholder="选择日期"
        />
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
  data () {
    return {
      date: '',
      pickerOptions: {
        disabledDate (time) {
          return time.getTime() > Date.now()
        },
        shortcuts: [{
          text: '今天',
          onClick (picker) {
            picker.$emit('pick', new Date())
          }
        }, {
          text: '昨天',
          onClick (picker) {
            const date = new Date()
            date.setTime(date.getTime() - 3600 * 1000 * 24)
            picker.$emit('pick', date)
          }
        }, {
          text: '一周前',
          onClick (picker) {
            const date = new Date()
            date.setTime(date.getTime() - 3600 * 1000 * 24 * 7)
            picker.$emit('pick', date)
          }
        }]
      },
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
        name: '部门'
      }, {
        id: 1,
        name: '路由'
      }, {
        id: 2,
        name: '角色'
      }, {
        id: 3,
        name: '员工'
      }, {
        id: 4,
        name: '权限'
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
    handleSearch () {
      this.$emit('search', this.formData)
    },
    handleReset () {
      const _this = this
      _this.formData = JSON.parse(JSON.stringify(_this.originalForm))
      console.log(_this.formData)
      console.log('重置参数')
      _this.$emit('search', _this.formData)
    },
    handleCreate () {
      this.$emit('create')
    }
  }
}
</script>
