<template>
  <div class="content-wrapper">
    <el-breadcrumb separator-class="el-icon-arrow-right">
      <el-breadcrumb-item :to="{ path: '/home' }">首页</el-breadcrumb-item>
      <el-breadcrumb-item>IO模型库</el-breadcrumb-item>
    </el-breadcrumb>
    <el-card>
      <el-row :gutter="20">
        <el-col :span="7">
          <el-input placeholder="请输入内容">
            <el-button slot="append" icon="el-icon-search"></el-button>
          </el-input>
        </el-col>
        <el-col :span="4">
          <el-button type="primary">add</el-button>
        </el-col>
      </el-row>
      <el-table :data="iolist" border stripe>
        <el-table-column prop="io_name" label="日期" width="180"></el-table-column>
        <el-table-column prop="io_tool" label="姓名" width="180"></el-table-column>
        <el-table-column prop="io_params" label="地址"></el-table-column>
      </el-table>
    </el-card>
  </div>
</template>

<script>
export default {
  data () {
    return {
      iolist: []
    }
  },
  created () {
    this.getIOModuleList()
  },
  methods: {
    async getIOModuleList () {
      const { data: res } = await this.$http.get('io')
      this.iolist = res
      console.log(this.iolist)
    }
  }
}
</script>

<style lang="less" scoped>
</style>
