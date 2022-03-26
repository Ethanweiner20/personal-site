<template>
  <div id="skills-container" class="page">
    <Header title="SKILLS" />

    <div id="table-container" class="mb-5">
      <table class="table table-dark text-start">
        <thead class="thead-light">
          <tr>
            <th scope="col">Skill</th>
            <th scope="col">Description</th>
            <th scope="col">Projects</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <th scope="row">
              <span>
                <img src="../assets/images/js_logo.png" width="20" alt="" />
              </span>
              Javascript
            </th>
            <td>Most familiar language for application development.</td>
            <td>
              <ul>
                <li>Visualize the Web</li>
                <li>Job Itinerary V1/V2/V3</li>
                <li>Scholarship Portal</li>
                <li>Playlist Blender</li>
              </ul>
            </td>
          </tr>
          <tr>
            <th scope="row">
              <span>
                <img src="../assets/images/vue_logo.png" width="20" alt="" />
              </span>
              Vue.js
            </th>
            <td>My web development framework of choice.</td>
            <td>
              <ul>
                <li>Job Itinerary</li>
                <li>Scholarship Portal</li>
              </ul>
            </td>
          </tr>
          <tr>
            <th scope="row">Other</th>
            <td colspan="2">
              <ul>
                <li>Familiar with Firebase (NoSQL) and SQL databases</li>
                <li>
                  Moderate experience programming in C, Java, Python, Racket,
                  and other languages.
                </li>
                <li>
                  Woekd with the Ionic cross-platform framework and UI kit
                </li>
                <li>Experience working with APIs</li>
                <li>
                  Basic frontend skills with HTML, css, bootstrap, material
                  design, etc.
                </li>
              </ul>
            </td>
          </tr>
        </tbody>
      </table>
    </div>

    <div
      class="d-none d-sm-block navigation navigate-right"
      @click="routeToWriting"
    >
      <div class="py-auto d-inline">
        <span>Writing</span>
      </div>
      <span
        class="material-icons material-icons-outlined"
        style="margin-left: 10px"
      >
        arrow_forward_ios
      </span>
    </div>
  </div>
</template>

<script>
import { useRouter } from 'vue-router'
import { transitionName } from '../store'
import Header from '../components/Header'

export default {
  name: 'Skills',
  components: {
    Header
  },
  setup() {
    const router = useRouter()
    const routeToWriting = () => {
      router.push({ name: 'Writing' })

      // Temporarily change the transition type
      transitionName.value = 'fade'
      setTimeout(() => {
        transitionName.value = 'zoom'
      }, 500)
    }
    return { routeToWriting }
  }
}
</script>

<style lang="scss">
@import '@/assets/styles.scss';
#skills-container {
  .navigate-right {
    div {
    }
  }
}
#table-container {
  position: absolute;
  top: 25%;
  @media (max-width: 500px) {
    top: 15%;
  }
  padding-left: 80px;
  padding-right: 125px;
  @media (max-width: 575px) {
    padding-left: 15px;
    padding-right: 15px;
  }
  width: 100%;
  color: white !important;
}
table {
  thead {
    font-size: 25px;
  }
  ul {
    text-align: left;
  }
  font-size: 20px;
  border: 3px solid $main-grey;
}
</style>
