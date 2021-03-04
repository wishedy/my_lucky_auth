<template>
  <span>
    <el-popover ref="pop" v-model="pop" :placement="placement" width="300" trigger="click">
      <el-collapse v-if="!searchMode" v-model="collapseActive" class="d2-icon-select--group">
        <el-row class="d2-icon-select--class-row">
          <el-col v-for="(iconName, iconIndex) in icon" :key="iconIndex" class="d2-icon-select--class-col" :span="4" @click.native="selectIcon(iconName)">
            <i :class="iconName" />
          </el-col>
        </el-row>
      </el-collapse>
    </el-popover>
    <!-- 允许用户输入 -->
    <el-input v-if="userInput" v-model="currentValue" v-bind="bind" style="max-width: 320px;">
      <template v-if="value" slot="prepend">
        <i :class="value" />
      </template>
      <el-button slot="append" v-popover:pop>
        <i class="el-icon-menu" />
      </el-button>
    </el-input>
    <!-- 不允许用户输入 -->
    <el-button v-if="!userInput" v-popover:pop>
      <template v-if="value">
        <i :class="value" />
      </template>
      {{ value ? value : placeholder }}
    </el-button>
  </span>
</template>

<script>
import icon from './index'
export default {
  name: 'D2IconSelect',
  props: {
    // 值
    value: {
      type: String,
      required: false,
      default: ''
    },
    // 占位符
    placeholder: {
      type: String,
      required: false,
      default: '请选择'
    },
    // 弹出界面的方向
    placement: {
      type: String,
      required: false,
      default: 'right'
    },
    // 是否可清空
    clearable: {
      type: Boolean,
      required: false,
      default: true
    },
    // 是否允许用户输入
    userInput: {
      type: Boolean,
      required: false,
      default: false
    },
    // 是否在选择后自动关闭
    autoClose: {
      type: Boolean,
      required: false,
      default: true
    }
  },
  data() {
    return {
      // 绑定弹出框
      pop: false,
      // 所有图标
      icon,
      // 组件内输入框的值
      currentValue: '',
      // 搜索的文字
      searchText: '',
      // 不是搜索的时候显示的折叠面板绑定的展开数据
      collapseActive: []
      // collapseActive: [...Array(icon.length)].map((e, i) => i)
    }
  },
  computed: {
    // 输入框上绑定的设置
    bind() {
      return {
        placeholder: this.placeholder,
        clearable: this.clearable,
        ...this.$attrs
      }
    },
    // 是否在搜索
    searchMode() {
      return !!this.searchText
    }
  },
  watch: {
    value(value) {
      this.currentValue = value
    }
  },
  created() {
    this.currentValue = this.value
  },
  methods: {
    selectIcon(iconName = '') {
      this.$emit('input', iconName)
      if (iconName && this.autoClose) {
        this.pop = false
      }
    }
  }
}
</script>

<style lang="scss" scoped>
// 主色
$color-primary: #409EFF;

// 辅助色
$color-info: #909399;
$color-success: #67C23A;
$color-warning: #E6A23C;
$color-danger: #F56C6C;

// 文字
$color-text-main: #303133;
$color-text-normal: #606266;
$color-text-sub: #909399;
$color-text-placehoder: #C0C4CC;

// 边框
$color-border-1: #DCDFE6;
$color-border-2: #E4E7ED;
$color-border-3: #EBEEF5;
$color-border-4: #F2F6FC;

// 背景
$color-bg: #f8f8f9;
.d2-icon-select--group {
  max-height: 400px;
  overflow-x: hidden;
  overflow-y: scroll;
  border-top: none;
  border-bottom: none;
  .d2-icon-select--class {
    .d2-icon-select--class-title {
      line-height: 30px;
      text-align: center;
      background-color: $color-bg;
      border-radius: 4px;
      margin: 10px 0px;
    }
    .d2-icon-select--class-row {
      padding: 10px;
      .d2-icon-select--class-col {
        line-height: 40px;
        text-align: center;
        color: $color-text-sub;
        &:hover {
          color: $color-text-main;
          background-color: $color-bg;
          border-radius: 4px;
          font-size: 26px;
          box-shadow: inset 0px 0px 0px 1px $color-border-1;
        }
      }
    }
  }
  .d2-icon-select--class-row{
    padding: 10px;
  }
  .d2-icon-select--class-col{
    font-size: 20px;
  }
}
</style>
