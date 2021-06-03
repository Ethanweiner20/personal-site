<template>
  <div
    :id="project_name"
    class="project carousel slide mx-auto mb-5 d-block"
    :class="mode == 'dark' ? 'carousel-dark' : ''"
    data-bs-ride="carousel"
    data-bs-interval="false"
  >
    <a :href="project_url" target="_blank" class="d-block">
      <h4 class="text-dark mt-2">{{ projectName }}</h4>
    </a>

    <div class="carousel-indicators">
      <button
        type="button"
        :data-bs-target="'#' + project_name"
        data-bs-slide-to="0"
        class="active"
        aria-current="true"
        aria-label="Slide 1"
      ></button>
      <button
        type="button"
        :data-bs-target="'#' + project_name"
        data-bs-slide-to="1"
        aria-label="Slide 2"
      ></button>
      <button
        type="button"
        :data-bs-target="'#' + project_name"
        data-bs-slide-to="2"
        aria-label="Slide 3"
      ></button>
    </div>
    <div class="carousel-inner" :href="project_url" target="_blank">
      <slot name="carousel-items"></slot>
    </div>
    <button
      class="carousel-control-prev"
      type="button"
      :data-bs-target="'#' + project_name"
      data-bs-slide="prev"
    >
      <span class="carousel-control-prev-icon" aria-hidden="true"></span>
      <span class="visually-hidden">Previous</span>
    </button>
    <button
      class="carousel-control-next"
      type="button"
      :data-bs-target="'#' + project_name"
      data-bs-slide="next"
    >
      <span class="carousel-control-next-icon" aria-hidden="true"></span>
      <span class="visually-hidden">Next</span>
    </button>
  </div>
</template>

<script>
import voca from 'voca'

export default {
  name: 'Project',
  props: ['project_name', 'project_url', 'mode'],
  data() {
    return {
      projectName: voca.titleCase(this.project_name).replace('-', ' ')
    }
  }
}
</script>

<style lang="scss">
@import '../assets/styles.scss';

.carousel {
  max-width: 650px;
  @media (max-width: 1500px) {
    max-width: 550px;
  }
  @media (max-width: 1270px) {
    max-width: 850px;
  }
  border: 5px solid $main-grey;
  border-radius: 5px;
  background: white;
}

.carousel-inner {
}
</style>
