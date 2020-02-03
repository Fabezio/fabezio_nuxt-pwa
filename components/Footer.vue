<template lang="pug">

  v-footer(v-bind='localAttrs', color="primary" :padless='padless')
    v-row
      // div(v-for='(link, i) in footerLinks', :key='i')
        nuxt-link.route(class='xl:hidden' :to='link.route')
          v-btn(icon)
            span.mr-2 {{link.icon}}
          v-btn(text)
            span.uppercase {{link.name }}

      a.indigo(href='https://github.com/Fabezio/my-website_tailwind-utility', target='_blank')
        v-btn(icon)
          span
            v-icon github
        v-btn(text)
          span.uppercase mon code source

      v-card.red.lighten-1.text-center(flat='', tile='', width='100%')
        v-card-text
          v-btn.mx-4(v-for='(icon, index) in socialNetworks', :key='index', icon='')
            v-img.social-icon(size='24px' :src='icon.logo' ) {{  }}
    v-row
      v-divider
      v-card-text.white--text
        | {{ new Date().getFullYear() }} —
        |
        strong fabezio
      //div.center-text {{ new Date().getFullYear() }}
        strong  &copy; fabezio.com
  //v-row.ma-12(align='center', justify='center')
    v-col(cols='12', md='8')
      v-select(v-model='variant', :items='items', clearable='', label='Variant')
      v-checkbox(v-model='padless', hide-details='', label='Padless')

  //footer.bg-purple-600.p-1.text-white.inset-x-0.border-t.border-purple-700
    nav.flex.items-center.justify-center.flex-wrap.pb-3
      //.flex.items-center.flex-shrink-0.text-white.mr-6



      div.mx-3 |
      a(v-for='(link, index) in socialNetworks' :key='index' :href='link.url' target='_blank')
        img.w-6.ml-2(:src='link.logo')

    div.footertext(cols='12')


</template>

<script>
import { mapState } from 'vuex'
// import IconStack from '@/components/IconStack'
export default {
  name: 'Footer',
  components: {
    // IconStack
  },
  data() {
    return {
      items: ['default', 'absolute', 'fixed'],
      padless: true,
      variant: 'fixed'
    }
  },
  computed: {
    ...mapState({
      footerLinks: (state) => state.links.footerLinks,
      socialNetworks: (state) => state.social.socialNetworks
    }),
    localAttrs() {
      const attrs = {}

      if (this.variant === 'default') {
        attrs.absolute = false
        attrs.fixed = false
      } else {
        attrs[this.variant] = true
      }
      return attrs
    }
  }
}
</script>

<style scoped>
.social-icon {
  width: 12px;
  height: 12px;
}
.footertext {
  text-align: center;
}
/*
  v-footer {
    margin: 0;
    padding: 0;
  }
*/
</style>
