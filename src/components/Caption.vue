<template>
  <div class="carousel-caption d-none d-md-block">
    <div class="external-links m-2 mb-4 d-inline-block">
      <a class="site-link p-1" :href="site_link" target="_blank"> Site Link </a>
      <a class="youtube-video-link p-1" :href="youtube_link" target="_blank">
        <img src="../assets/images/yt_icon_mono_dark.png" alt="" width="20" />
        Youtube Tutorial
      </a>
      <a class="github-repo-link p-1" :href="github_link" target="_blank">
        <img src="../assets/images/GitHub-Mark-32px.png" alt="" width="20" />
        Github Repo
      </a>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Caption',
  props: ['site_link', 'youtube_link', 'github_link']
}
</script>

<style lang="scss">
a {
  margin-right: 6px;
}
a.youtube-video-link {
  background: red;
  color: white;
  border-radius: 5px;
  z-index: 100 !important;
  &:hover {
    background: lighten(red, 20);
    color: white;
  }
}

a.github-repo-link {
  background: white;
  color: #23282d;
  border-radius: 5px;
  &:hover {
    background: rgb(202, 202, 202);
    color: #23282d;
  }
}

a.site-link {
  background: rgb(179, 167, 0);
  color: white;
  border-radius: 5px;
  &:hover {
    background: lighten(rgb(179, 167, 0), 10);
    color: white;
  }
}

.carousel-caption {
  background: rgba(1, 1, 1, 0.8);
  padding: 8px;
  border-radius: 50px;
  margin-bottom: -10px;
}
</style>
