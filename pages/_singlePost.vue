<template>
  <div id="post-page" class="page-wrapper post-page">
    <site-hero :title="title" :subtitle="subtitle" :image="featureImage">
      <span
        v-if="author && $siteConfig.posts.displayAuthor"
        class="author-wrapper"
      >
        <strong>Autor:</strong> {{ author }}
      </span>
      <span v-if="date" class="date-wrapper">
        <strong>Publicado en:</strong> {{ date }}
      </span>
    </site-hero>
    <main-section :one-column-constrained="true">
      <template v-slot:default>
        <div class="post-wrapper">
          <markdown :markdown="$store.state.content" />
          <article class="message is-warning">
            <div class="message-header">
              <p>¿Quieres añadir algo más?</p>
            </div>
            <div class="message-body">
              Entra este proyecto de Github y envía una issue:
              <a href="https://github.com/delineas/teletrabajando-web/issues"
                >teletrabajando-web</a
              >
            </div>
          </article>
          <div class="other-posts">
            <h6 class="subtitle is-size-4">
              Relacionado
            </h6>
            <!-- Related Posts -->
            <posts-grid :number="3" :category="category" :exclude="slug" />
          </div>
          <disqus-comments :identifier="$route.params.singlePost" />
        </div>
      </template>
      <template v-slot:sidebar>
        <post-sidebar />
      </template>
    </main-section>
  </div>
</template>
<script>
import { mapState } from 'vuex'
import { setPageData, getFormattedDate } from '../helper'
// import 'highlight.js/styles/github.css'
import Markdown from '~/components/Markdown'
import PostSidebar from '~/components/PostSidebar'

export default {
  components: {
    Markdown,
    PostSidebar
  },
  head() {
    return {
      meta: [
        {
          hid: 'og:image',
          property: 'og:image',
          content: `https://teletrabajando.webreactiva.com${this.responsiveImage}`
        }
      ]
    }
  },
  computed: {
    ...mapState([
      'title',
      'subtitle',
      'featureImage',
      'underSubtitle',
      'author',
      'category',
      'slug'
    ]),
    date() {
      return getFormattedDate(this.$store.state.date)
    },
    url() {
      return `${process.env.URL}/${this.$route.fullPath}`
    },
    responsiveImage() {
      if (this.featureImage.indexOf('/uploads') === 0) {
        return require(`~/assets${this.featureImage}`)
      }
      return { src: this.featureImage, srcSet: '' }
    },
  },
  fetch({ store, params }) {
    setPageData(store, { resource: 'post', slug: params.singlePost })
  }
}
</script>
<style scoped lang="scss">
.edit-post {
  margin-bottom: 20px;
}
</style>
