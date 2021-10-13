<template>
  <v-app>
    <v-app-bar app color="primary" dark>
      <v-app-bar-nav-icon @click="drawer = !drawer" />
      <SiteTitle :title="title"></SiteTitle>
      <v-spacer />
    </v-app-bar>
    <v-navigation-drawer app v-model="drawer">
      <v-divider></v-divider>
      <SiteMenu></SiteMenu>

      <v-list dense nav></v-list>
    </v-navigation-drawer>
    <v-content>
      <router-view />
    </v-content>
    <SiteFooter :footer="footer"></SiteFooter>
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
      title: 'KAI CERTIFICATION',
      footer: 'KAI Certification Inc.'
    }
  }

}
</script>
