<template>
  <div class="app-container">
    <div style="padding-bottom: 25px">
      <el-row :gutter="0">
        <el-col :xs="{span: 24}" :sm="{span: 24}" :md="{span: 24}" :lg="{span: 24}" :xl="{span: 24}" style="margin-bottom:30px;">
          <div class="lesson-container">
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
        </el-col>
      </el-row>
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
      mp3Url: '',
      pdfUrl: '',
      currentPage: 1,
      pageCount: 1,
      lessonId: ''
    }
  },
  created() {
    this.getLesson()
  },
  methods: {
    getLesson() {
      const { id } = this.$route.params
      this.lessonId = id
      this.mp3Url = `/static/lesson/${this.lessonId}/${this.lessonId}.mp3`
      this.pdfUrl = `/static/lesson/${this.lessonId}/${this.lessonId}.pdf`
      // Debug
      console.log(`this.lessonId = ${this.lessonId}`)
      console.log(`this.mp3Url = ${this.mp3Url}`)
      console.log(`this.pdfUrl = ${this.pdfUrl}`)
    },
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
.lesson-container {
  /* width: 350px; */
  position: relative;
}
</style>
