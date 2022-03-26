<template>
  <div id="writing-container" class="page text-left">
    <Header title="WRITING" />
    <div class="medium-container text-left">
      <div
        id="retainable-rss-embed"
        data-rss="https://medium.com/feed/@ethanweiner"
        data-maxcols="3"
        data-layout="slider"
        data-poststyle="modal"
      ></div>
    </div>

    <div
      class="d-none d-sm-block navigation navigate-right"
      @click="routeToProjects"
    >
      <div class="py-auto d-inline">
        <span>Projects</span>
      </div>
      <span class="material-icons material-icons-outlined">
        arrow_forward_ios
      </span>
    </div>
  </div>
</template>

<script>
import { useRouter } from 'vue-router'
import { transitionName } from '../store'
import Project from '../components/Project'
import Caption from '../components/Caption'
import Header from '../components/Header'
import { onMounted } from '@vue/runtime-core'

export default {
  name: 'Projects',
  components: {
    Project,
    Caption,
    Header
  },
  setup() {
    const router = useRouter()
    const routeToProjects = () => {
      router.push({ name: 'Projects' })

      // Temporarily change the transition type
      transitionName.value = 'fade'
      setTimeout(() => {
        transitionName.value = 'zoom'
      }, 500)
    }

    // Code taken from twilik
    onMounted(() => {
      var container = document.getElementById('retainable-rss-embed')
      if (container) {
        var css = document.createElement('link')
        css.href =
          'https://www.twilik.com/assets/retainable/rss-embed/retainable.css'
        css.rel = 'stylesheet'
        document.getElementsByTagName('head')[0].appendChild(css)
        var script = document.createElement('script')
        script.src =
          'https://www.twilik.com/assets/retainable/rss-embed/retainable.js'
        document.getElementsByTagName('body')[0].appendChild(script)
      }
    })

    return { routeToProjects }
  }
}
</script>

<style lang="scss">
@import '@/assets/styles.scss';

.medium-container {
  margin: 50px;
  margin-right: 100px;
  padding: 30px;
  border: 5px solid $main-color;
  text-align: left !important;
  border-radius: 5px;
}

.medium-container h2 {
  margin-top: 20px;
  margin-bottom: 0;
}

.read-more {
  text-align: left !important;
}
</style>
