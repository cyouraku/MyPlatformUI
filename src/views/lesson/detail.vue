<template>
  <div class="app-container">
    <div style="padding-bottom: 25px">
      <el-row :gutter="0" type="flex" justify="center">
        <el-col :xs="{span: 8}" :sm="{span: 8}" :md="{span: 8}" :lg="{span: 8}" :xl="{span: 8}">
          <el-button type="primary" @click="changePrev">Prev</el-button>
        </el-col>
        <el-col :xs="{span: 8}" :sm="{span: 8}" :md="{span: 8}" :lg="{span: 8}" :xl="{span: 8}">
          <el-button type="info" disabled>Current Page: {{ currentPage }}</el-button>
        </el-col>
        <p style="width: 60px" />
        <el-col :xs="{span: 8}" :sm="{span: 8}" :md="{span: 8}" :lg="{span: 8}" :xl="{span: 8}">
          <el-button type="primary" @click="changeNext">Next</el-button>
        </el-col>
      </el-row>
      <el-row :gutter="0">
        <el-col :xs="{span: 24}" :sm="{span: 24}" :md="{span: 24}" :lg="{span: 24}" :xl="{span: 24}">
          <div class="lesson-container">
            <pdf
              :src="pdfUrl"
              :page="currentPage"
              class="page-set"
              @num-pages="pageCount = $event"
              @page-loaded="currentPage = $event"
            />
          </div>
          <!-- <vue-audio :file="mp3Url" /> -->
          <audio controls>
            <source :src="mp3Url" type="audio/ogg">
          </audio>
        </el-col>
      </el-row>
    </div>
  </div>
</template>

<script>
import pdf from 'vue-pdf'

export default {
  name: 'LessonDemo',
  components: { pdf },
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
