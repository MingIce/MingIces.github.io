<template>
  <div>
  <div class="block">
    <!--<span class="demonstration">开始日期：</span>-->
    <!-- 焦点离开文本框就触发change方法 -->
    <el-date-picker v-model="value1" type="date" placeholder="选择日期" v-on:blur="change">
    </el-date-picker>
  </div>
 <!-- <div class="block">
    <span class="demonstration">带快捷选项</span>
    <el-date-picker
      v-model="value2"
      align="right"
      type="date"
      placeholder="选择日期"
      :picker-options="pickerOptions1">
    </el-date-picker>
  </div>-->
  </div>
</template>

<script>
export default {
  data() {
    return {
      pickerOptions1: {
        disabledDate(time) {
          return time.getTime() > Date.now()
        },
        shortcuts: [{
          text: '今天',
          onClick(picker) {
            picker.$emit('pick', new Date())
          }
        }, {
          text: '昨天',
          onClick(picker) {
            const date = new Date()
            date.setTime(date.getTime() - 3600 * 1000 * 24)
            picker.$emit('pick', date)
          }
        }, {
          text: '一周前',
          onClick(picker) {
            const date = new Date()
            date.setTime(date.getTime() - 3600 * 1000 * 24 * 7)
            picker.$emit('pick', date)
          }
        }]
      },
      value1: '',
      value2: ''
    }
  },
  methods: {
    change: function() {
      /* 传递到父组件 */
      this.$emit('on-change', this.value1)
    }
  }
}
</script>
