<template>
  <li :ref="'link-' + name" class="my-2">
    <a
      class="collapse-link"
      data-bs-toggle="collapse"
      :href="'#collapse-' + name"
      role="button"
      aria-expanded="false"
      aria-controls="collapse-1"
    >
      <span class="fw-bold mission-name">
        <slot name="mission-name"></slot>
      </span>
      <span
        class="material-icons material-icons-outlined collapse-button"
        :ref="'arrow' + name"
        >expand_more</span
      >
    </a>

    <div class="collapse" :id="'collapse-' + name">
      <p>
        <slot name="mission-description"></slot>
      </p>
    </div>
  </li>
</template>

<script>
export default {
  name: 'Misson',
  props: ['name'],
  mounted() {
    const link = this.$refs['link-' + this.name]
    const arrow = this.$refs['arrow' + this.name]

    // Switch arrow type upon click
    link.addEventListener('click', (e) => {
      if (arrow.innerHTML == 'expand_more') arrow.innerHTML = 'expand_less'
      else arrow.innerHTML = 'expand_more'
    })
  }
}
</script>

<style lang="scss">
@import '../assets/styles.scss';
.collapse-button {
  font-size: 50px !important;
  @media (max-width: 575px) {
    font-size: 40px !important;
  }
  vertical-align: bottom;
  color: $main-color;
  &:hover {
    color: lighten($main-color, 10);
  }
}
.collapse-link {
  color: white;
  &:hover {
    color: white;
  }

  .mission-name {
    font-size: 28px;
    @media (max-width: 575px) {
      font-size: 23px;
    }
  }
}
</style>
