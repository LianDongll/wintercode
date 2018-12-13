<template>
  <el-dialog title="数据概览"
             :visible.sync="show" 
             fullscreen>
              <!--
               .sync 只是一个双向绑定的语法糖，是指允许子组件内部修改父组件的状态 
               组件el-dialog 的visible 状态可以被组件内部改变
               -->
    <overview></overview>
  </el-dialog>
</template>

<script>
import overview from '@/components/overview'
export default {
  name: 'overviewDialog',
  components: {
    overview
  },
  data() {
    return {
      show: false
    }
  },
  props: {
    showFlag: {
      type: Boolean,
      required: true
    }
  },
  mounted() {
    this.show = this.showFlag
  },
  watch: {
    show: function(newV, oldV) {
      this.$emit('closeDialog', newV)
    },
    showFlag: function(newV, oldV) {
      this.show = newV
    }
  }
}
</script>

<style>
</style>
