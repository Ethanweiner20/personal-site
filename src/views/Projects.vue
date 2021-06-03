<template>
  <div id="project-container" class="page text-left">
    <Header title="PROJECTS" />

    <div id="projects" class="p-5">
      <!-- Playlist Blender -->
      <Project
        project_name="playlist-blender"
        project_url="https://playlistblender.com"
        mode="light"
      >
        <template v-slot:carousel-items>
          <div class="carousel-item active">
            <img
              src="../assets/images/playlist_blender_3.png"
              alt="Job Itinerary"
              class="d-block w-100"
            />
            <Caption
              site_link="https://playlistblender.com"
              youtube_link="https://youtu.be/hqWAYC8PWxg"
              github_link="https://github.com/Ethanweiner20/playlist-blender"
            />
          </div>
          <div class="carousel-item">
            <img
              src="../assets/images/playlist_blender_1.png"
              alt="Job Itinerary"
              class="d-block w-100"
            />
          </div>
          <div class="carousel-item">
            <img
              src="../assets/images/playlist_blender_2.png"
              alt="Job Itinerary"
              class="d-block w-100"
            />
          </div>
        </template>
      </Project>

      <!-- Job Itinerary -->
      <Project
        project_name="job-itinerary"
        project_url="https://jobitinerary.com/"
        mode="dark"
      >
        <template v-slot:carousel-items>
          <div class="carousel-item active">
            <img
              src="../assets/images/job_itinerary_1.png"
              alt="Job Itinerary"
              class="d-block w-100"
            />
            <Caption
              site_link="https://jobitinerary.com/"
              youtube_link="https://youtu.be/ih-i5kAkeRw"
              github_link="https://github.com/Ethanweiner20/job_itinerary"
            />
          </div>
          <div class="carousel-item">
            <img
              src="../assets/images/job_itinerary_2.png"
              alt="Job Itinerary"
              class="d-block w-100"
            />
          </div>
          <div class="carousel-item">
            <img
              src="../assets/images/job_itinerary_3.png"
              alt="Job Itinerary"
              class="d-block w-100"
            />
          </div>
        </template>
      </Project>

      <Project
        project_name="scholarship-portal"
        project_url="https://bhs-scholarship-portal.web.app/"
        mode="dark"
      >
        <template v-slot:carousel-items>
          <div class="carousel-item active">
            <img
              src="../assets/images/bhs_scholarship_portal1.png"
              alt="Scholarship Portal"
              class="d-block w-100"
            />
            <Caption
              site_link="https://bhs-scholarship-portal.web.app/"
              youtube_link="https://www.youtube.com/watch?v=IBISBFMGAiI"
              github_link="https://github.com/Ethanweiner20/bhs-scholarship-portal"
            />
          </div>
          <div class="carousel-item">
            <img
              src="../assets/images/bhs_scholarship_portal3.png"
              alt="Scholarship Portal"
              class="d-block w-100"
            />
          </div>
          <div class="carousel-item">
            <img
              src="../assets/images/bhs_scholarship_portal4.png"
              alt="Scholarship Portal"
              class="d-block w-100"
            />
          </div>
        </template>
      </Project>
    </div>

    <div
      class="d-none d-sm-block navigation navigate-right"
      @click="routeToSkills"
    >
      <div class="py-auto d-inline">
        <span>Skills</span>
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

export default {
  name: 'Projects',
  components: {
    Project,
    Caption,
    Header
  },
  setup() {
    const router = useRouter()
    const routeToSkills = () => {
      router.push({ name: 'Skills' })

      // Temporarily change the transition type
      transitionName.value = 'fade'
      setTimeout(() => {
        transitionName.value = 'zoom'
      }, 500)
    }
    return { routeToSkills }
  }
}
</script>

<style lang="scss">
@import '@/assets/styles.scss';

#projects {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-around;
  @media (min-width: 576px) {
    padding-right: 120px !important;
  }
}
</style>
