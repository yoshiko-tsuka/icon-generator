<template>
  <v-app id="inspire">
    <v-navigation-drawer
      v-model="drawer"
      app
    >
      <v-list dense>
        <v-list-group no-action sub-group>
          <template v-slot:activator>
            <v-list-item-content>
              <v-list-item-title><v-icon color="pink lighten-3">favorite</v-icon></v-list-item-title>
            </v-list-item-content>
          </template>
          <v-list-item style="padding-left:0px;">
            <svg id="artboard" xmlns="http://www.w3.org/2000/svg" style="border: medium solid #ffffff;" width="300" height="100" viewbox="100 0 300 100">
              <circle cx=50 cy=50 r=40 fill="blue"/>
              <rect x="100" y="14" rx="0" ry="0" width="75" height="75" stroke-width="1" stroke="blue" fill="blue"/>
            </svg>
          </v-list-item>
          <v-list-item style="padding-left:0px;">
            <svg id="artboard" xmlns="http://www.w3.org/2000/svg" style="border: medium solid #ffffff;" width="300" height="100" viewbox="100 0 300 100">
              <circle cx=50 cy=50 r=40 fill="blue"/>
              <rect x="100" y="50" rx="0" ry="0" width="50" height="40" stroke-width="1" stroke="#00FFFF" fill="#CCFFFF"/>
            </svg>
          </v-list-item>
        </v-list-group>
        <v-list-group no-action sub-group>
          <template v-slot:activator>
            <v-list-item-content>
              <v-list-item-title><v-icon color="blue darken-2">remove</v-icon></v-list-item-title>
            </v-list-item-content>
          </template>
          <v-list-item style="padding-left:0px;">
            <svg id="artboard" xmlns="http://www.w3.org/2000/svg" style="border: medium solid #ffffff;" width="300" height="100" viewbox="100 0 300 100">
              <circle cx=50 cy=50 r=40 fill="blue"/>
              <rect x="100" y="14" rx="0" ry="0" width="75" height="75" stroke-width="1" stroke="blue" fill="blue"/>
            </svg>
          </v-list-item>
          <v-list-item style="padding-left:0px;">
            <svg id="artboard" xmlns="http://www.w3.org/2000/svg" style="border: medium solid #ffffff;" width="300" height="100" viewbox="100 0 300 100">
              <circle cx=50 cy=50 r=40 fill="blue"/>
              <rect x="100" y="50" rx="0" ry="0" width="50" height="40" stroke-width="1" stroke="#00FFFF" fill="#CCFFFF"/>
            </svg>
          </v-list-item>
        </v-list-group>
        <v-list-group no-action sub-group>
          <template v-slot:activator>
            <v-list-item-content>
              <v-list-item-title><v-icon color="orange darken-1">tag_faces</v-icon></v-list-item-title>
            </v-list-item-content>
          </template>
          <v-list-item style="padding-left:0px;">
            <svg id="artboard" xmlns="http://www.w3.org/2000/svg" style="border: medium solid #ffffff;" width="300" height="100" viewbox="100 0 300 100">
              <circle cx=50 cy=50 r=40 fill="blue"/>
              <rect x="100" y="14" rx="0" ry="0" width="75" height="75" stroke-width="1" stroke="blue" fill="blue"/>
            </svg>
          </v-list-item>
          <v-list-item style="padding-left:0px;">
            <svg id="artboard" xmlns="http://www.w3.org/2000/svg" style="border: medium solid #ffffff;" width="300" height="100" viewbox="100 0 300 100">
              <circle cx=50 cy=50 r=40 fill="blue"/>
              <rect x="100" y="50" rx="0" ry="0" width="50" height="40" stroke-width="1" stroke="#00FFFF" fill="#CCFFFF"/>
            </svg>
          </v-list-item>
        </v-list-group>
        <v-list-group no-action sub-group>
          <template v-slot:activator>
            <v-list-item-content>
              <v-list-item-title><v-icon>brush</v-icon></v-list-item-title>
            </v-list-item-content>
          </template>
          <v-list-item>
            <v-list-item-content>
              <v-list-item-title>Coming Soon!!</v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </v-list-group>
        <v-list-group no-action sub-group>
          <template v-slot:activator>
            <v-list-item-content>
              <v-list-item-title><v-icon>text_rotation_none</v-icon></v-list-item-title>
            </v-list-item-content>
          </template>
          <v-list-item>
            <v-list-item-content>
              <v-list-item-title>Coming Soon!!</v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </v-list-group>
        <v-list-group no-action sub-group>
          <template v-slot:activator>
            <v-list-item-content>
              <v-list-item-title><v-icon>add_photo_alternate</v-icon></v-list-item-title>
            </v-list-item-content>
          </template>
          <v-list-item>
            <v-list-item-content>
              <v-list-item-title>Coming Soon!!</v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </v-list-group>
      </v-list>
    </v-navigation-drawer>

    <v-app-bar
      app
      color="pink lighten-1"
    >
      <v-app-bar-nav-icon class="white--text" @click.stop="drawer = !drawer"></v-app-bar-nav-icon>
      <v-toolbar-title class="white--text">Icon Generator</v-toolbar-title>
    </v-app-bar>

    <v-content>
      <v-container>
        <v-row>
          <v-col class="text-center">
            <nuxt />
          </v-col>
        </v-row>
      </v-container>
    </v-content>
    
    <v-footer
      color="pink lighten-1"
      app
    >
      <span class="white--text">&copy; {{ year }}</span>
    </v-footer>
  </v-app>
</template>

<script>
  export default {
    props: {
      source: String,
    },
    data: () => ({
      drawer: null,
      year: 2020,
    }),
    mounted () {
      const today = new Date()
      this.year = today.getFullYear()
    }
  }
</script>