<template>
  <v-app>
    <v-app-bar app color="primary" dark>
      <v-app-bar-nav-icon @click="drawer = !drawer" />
      <SiteTitle :title="site.title"></SiteTitle>
      <v-spacer />
    </v-app-bar>
    <v-navigation-drawer app v-model="drawer">
      <v-divider></v-divider>
      <SiteMenu :items="site.menu"></SiteMenu>

      <v-list dense nav></v-list>
    </v-navigation-drawer>
    <v-main>
      <router-view />
    </v-main>
    <SiteFooter :footer="site.footer"></SiteFooter>
  </v-app>
</template>

<script>
import SiteTitle from '@/views/site/Title.vue'
import SiteFooter from '@/views/site/Footer.vue'
import SiteMenu from '@/views/site/Menu.vue'

export default {
  name: 'App',
  components: {
    SiteTitle,
    SiteFooter,
    SiteMenu
  },

  data () {
    return {
      drawer: false,
      site: {
        menu: [{
          title: 'Home',
          icon: 'mdi-home',
          subItems: [
            {
              title: 'Dashboard',
              to: '/'
            }
          ]
        },
        {
          title: 'Who we are',
          icon: 'mdi-tag',
          active: 'true',
          subItems: [
            {
              title: 'About',
              to: '/about'
            }
          ]
        }],
        title: 'KAI CERTIFICATION',
        footer: 'KAI Certification Inc.'
      }

    }
  },
  created () {
    this.subscribe()
  },
  methods: {
    subscribe () {
      this.$firebase.database().ref().child('site').on('value', (sn) => {
        const v = sn.val()
        if (!v) {
          this.$firebase.database().ref().child('site').set(this.site)
          return
        }
        this.site = v
      }, err => {
        console.log(err.message)
      })
    }
  }
}

</script>
