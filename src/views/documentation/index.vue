<template>
  <div class="app-container documentation-container">
    <div v-if="checkPermission(['admin'])">
      <draggable
        :list="articleList"
        v-bind="$attrs"
      >
        <div
          v-for="(item, index) in articleList"
          :key="index"
        >
          <dropdown-menu
            :items="item.articles"
            style="float:left;margin-left:50px;"
            :title="item.name"
          />
        </div>
      </draggable>
    </div>
    <div v-if="checkPermission(['editor'])">
      <draggable
        :list="lessonList"
        v-bind="$attrs"
      >
        <div
          v-for="(item, index) in lessonList"
          :key="index"
        >
          <dropdownMenu4Lesson
            :items="item.articles"
            style="float:left;margin-left:50px;"
            :title="item.name"
          />
        </div>
      </draggable>
    </div>
  </div>
</template>
<script>
import checkPermission from '@/utils/permission'
import DropdownMenu from '@/components/Share/dropdownMenu'
import DropdownMenu4Lesson from '@/components/Share/dropdownMenu4Lesson'
import draggable from 'vuedraggable'
import articleList from './articleList'
import lessonList from './lessonList'

export default {
  name: 'Documentation',
  components: { DropdownMenu, DropdownMenu4Lesson, draggable },
  data() {
    return {
      // name & title max 10 varchar.
      articleList: articleList,
      lessonList: lessonList
    }
  },
  methods: {
    checkPermission
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
