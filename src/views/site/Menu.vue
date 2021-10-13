<template>
  <div>
    <v-list-item>
      <v-list-item-content>
        <v-list-item-title class="title">Application</v-list-item-title>
        <v-list-item-subtitle>subtext</v-list-item-subtitle>
      </v-list-item-content>
    </v-list-item>
    <v-list>
      <v-list-group
        v-for="(item,i) in items"
        :key="i"
        v-model="item.active"
        :prepend-icon="item.icon"
        no-action
      >
        <template v-slot:activator>
          <v-list-item-content>
            <v-list-item-title v-text="item.title"></v-list-item-title>
          </v-list-item-content>
        </template>

        <v-list-item v-for="subItems in item.subItems" :key="subItems.title" :to="subItems.to">
          <v-list-item-content>
            <v-list-item-title v-text="subItems.title"></v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list-group>
    </v-list>
  </div>
</template>

<script>
export default {
  props: ['footer'],
  data () {
    return {
      items: [
        {
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

        }
      ]
    }
  }

}
</script>

<style>
</style>
