<template lang="pug">
//- v-menu(:close-on-content-click='false' bottom='' left='' min-width='300' max-width='300' nudge-left='12' offset-x='' transition='slide-y-transition')
//-   v-btn.elevation-0(slot='activator' color='grey' dark='' fab='' fixed='' style='top: 96px;' top='')
//-     v-icon mdi-settings
//-   v-card
//-     v-container(grid-list-xl='')
//-       v-layout(wrap='')
//-         v-flex(xs12='')
//-           .text-xs-center.body-2.text-uppercase.sidebar-filter Sidebar Filters
//-           v-layout(justify-center='')
//-             v-avatar(v-for='c in colors' :key='c' :class="[c === color ? 'color-active color-' + c: 'color-' + c]" size='23' @click='setColor(c)')
//-           v-divider.mt-3
//-         v-flex(xs12='')
//-           .text-xs-center.body-2.text-uppercase.sidebar-filter Images
//-         v-flex(v-for='img in images' :key='img' xs3='')
//-           v-img(:class="[image === img ? 'image-active' : '']" :src='img' height='120' @click.native='setImage(img)')
//-         v-flex(xs12='')
//-           v-btn(href='https://www.creative-tim.com/product/vuetify-material-dashboard' target='_blank' color='success' block='')
//-             | Free Download
//-         v-flex(xs12='')
//-           v-btn.white--text(href='https://demos.creative-tim.com/vuetify-material-dashboard/documentation' target='_blank' color='primary' block='')
//-             | Documentation
//-         v-flex(xs12='')
//-           .text-xs-center.body-2.text-uppercase
//-             .sidebar-filter
//-               | Thank You for Sharing!
//-             div
//-               v-btn.mr-2.v-btn-facebook(color='indigo' fab='' icon='' small='' round='')
//-                 v-icon mdi-facebook
//-               v-btn.v-btn-twitter(color='cyan' fab='' icon='' small='' round='')
//-                 v-icon mdi-twitter

</template>

<script>
// Utilities
import {
  mapMutations,
  mapState
} from 'vuex'

export default {
  data: () => ({
    colors: [
      'primary',
      'info',
      'success',
      'warning',
      'danger'
    ],
    images: [
      'https://demos.creative-tim.com/vue-material-dashboard/img/sidebar-1.23832d31.jpg',
      'https://demos.creative-tim.com/vue-material-dashboard/img/sidebar-2.32103624.jpg',
      'https://demos.creative-tim.com/vue-material-dashboard/img/sidebar-3.3a54f533.jpg',
      'https://demos.creative-tim.com/vue-material-dashboard/img/sidebar-4.3b7e38ed.jpg'
    ]
  }),

  computed: {
    ...mapState('app', ['image', 'color']),
    color () {
      return this.$store.state.app.color
    }
  },

  methods: {
    ...mapMutations('app', ['setImage']),
    setColor (color) {
      this.$store.state.app.color = color
    }
  }
}
</script>

<style lang="scss">
  .v-avatar,
  .v-responsive {
    cursor: pointer;
  }
</style>
