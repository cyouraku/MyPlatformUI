<template>
  <div class="app-container">
    <div style="padding-bottom: 25px">
      <div>
        <span>
          <el-button type="primary" @click="changePrev">Prev</el-button>
        </span>
        <span>
          <el-button type="primary" @click="changeNext">Next</el-button>
        </span>
        <pdf
          :src="pdfUrl"
          :page="currentPage"
          class="page-set"
          @num-pages="pageCount = $event"
          @page-loaded="currentPage = $event"
        />
      </div>
      <vue-audio :file="mp3Url" />
    </div>
  </div>
</template>

<script>
import VueAudio from 'vue-audio'
import pdf from 'vue-pdf'

export default {
  name: 'LessonDemo',
  components: { VueAudio, pdf },
  data() {
    return {
      mp3Url: '/static/lesson/01_01/01_01.mp3',
      pdfUrl: '/static/lesson/01_01/01_01.pdf',
      currentPage: 1,
      pageCount: 1
    }
  },
  methods: {
    changePrev() {
      if (this.currentPage > 1) {
        this.currentPage--
      }
    },
    changeNext() {
      if (this.currentPage < this.pageCount) {
        this.currentPage++
      }
    }
  }
}
</script>

<style scoped>
.pdf-set {
  display: inline-block;
  width: 80%;
  position: relative;
  align-self: center;
}
</style>
