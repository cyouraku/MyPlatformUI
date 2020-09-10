<template>
  <div class="app-container documentation-container">
    <dropdown-menu :items="articleList" style="float:left;margin-left:50px;" title="CukeTest" />
  </div>
</template>
<script>
import DropdownMenu from '@/components/Share/dropdownMenu'

export default {
  name: 'Documentation',
  components: { DropdownMenu },
  data() {
    return {
      articleList: [
        { title: '概述', href: 'http://cuketest.com/zh-cn/bdd/' },
        { title: '剧本文件编辑', href: 'http://cuketest.com/zh-cn/features/' },
        { title: '代码编辑', href: 'http://cuketest.com/zh-cn/codes/' },
        { title: '执行及测试报告', href: 'http://cuketest.com/zh-cn/execution/' },
        { title: '模型管理器', href: 'http://cuketest.com/zh-cn/model_mgr/' },
        { title: '自动化API', href: 'http://cuketest.com/zh-cn/node_api/' },
        { title: 'Qt自动化', href: 'http://cuketest.com/zh-cn/qt/' },
        { title: '其它主题', href: 'http://cuketest.com/zh-cn/misc/' }
      ]
    }
  }
}
</script>

<style lang="scss" scoped>
.documentation-container {
  margin: 50px;
  .document-btn {
    float: left;
    margin-left: 50px;
    display: block;
    cursor: pointer;
    background: black;
    color: white;
    height: 60px;
    width: 200px;
    line-height: 60px;
    font-size: 20px;
    text-align: center;
  }
}
</style>
