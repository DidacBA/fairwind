<template>
  <div class="copy-and-gallery bg-fairwind-medium-blue pb-24">
    <div class="video-container v-full bg-cover bg-center text-white" :style="{ backgroundImage: `url(${videoThumbnail})` }">
      <div class="p-32">
        <a v-if="showVideoLink" :href="content.videourl" target="_blank" class="text-6xl" rel="noreferrer">
          <span class="sr-only">Link to boat video</span>
          <font-awesome-icon :icon="{ prefix: 'fab', iconName: 'youtube' } "/>
        </a>
      </div>
      <div class="container mx-auto flex justify-end">
        <h2 class="font-page-title text-6xl px-4 text-shadow">Our Flagship</h2>
      </div>
    </div>
    <div class="copy container mx-auto px-4">
      <p class="text-left text-white font-light py-8">"{{ content.body }}</p>
      <div class="boat-gallery-wrapper py-4">
        <client-only>
          <vue-picture-swipe :items="images" />
          <template slot="placeholder">
            <div class="my-gallery">
              <figure></figure>
              <a></a>
              <img></img>
            </div>
          </template>
        </client-only>
      </div>
    </div>
  </div>
</template>

<script>
import DividerBottom from '@/components/general/DividerBottom'
export default {
  components: {
    DividerBottom
  },
  data() {
    return {
      showVideoLink: true,
    }
  },
  computed: {
    content() {
      return this.$store.state.siteContent.flagship
    },
    images() {
      const { images } = this.$store.state.siteContent.flagship;
      return images.map((img) => ({
        src: img.src,
        thumbnail: img.src,
        w: 1200,
        h: 900,
        alt: img.alt
      }));
    },
    videoThumbnail() {
      const { videourl, useThumbnail, fallbackImg } = this.$store.state.siteContent.flagship
      if (videourl && useThumbnail) {
        const id = videourl.split('watch?v=').pop();
        return `https://img.youtube.com/vi/${id}/maxresdefault.jpg`
      }
      if (videourl && fallbackImg) {
        return fallbackImg
      }
      if (!videourl) {
        this.showVideoLink = false
        return fallbackImg
      }
    }
  },
}
</script>

<style lang="css">
.boat-gallery-wrapper .my-gallery {
  display: grid;
  grid-template-columns: 33.3% 33.3% 33.3%;
}
.boat-gallery-wrapper .my-gallery figure {
  flex-grow: 1;
  min-width: 20%;
  margin-left: 5px;
  margin-right: 5px;
}
.boat-gallery-wrapper .my-gallery figure a img {
  border-radius: 1px;
}
.boat-gallery-wrapper .my-gallery figure a img:hover {
  transform: scale(1.05);
  transition: all 0.15s ease-in-out;
}
</style>