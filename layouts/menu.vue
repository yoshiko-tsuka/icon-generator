<template>
  <v-app>
    <v-navigation-drawer
      v-model="drawer"
      :mini-variant.sync="mini"
      absolute
      permanent
    >
      <v-list-item class="px-2">
        <v-list-item-avatar>
          <v-img src="https://randomuser.me/api/portraits/men/85.jpg"></v-img>
        </v-list-item-avatar>

        <v-list-item-title>John Leider</v-list-item-title>

        <v-btn
          icon
          @click.stop="mini = !mini"
        >
          <v-icon>mdi-chevron-left</v-icon>
        </v-btn>
      </v-list-item>

      <v-divider></v-divider>

      <v-list dense>
        <v-list-group no-action sub-group>
          <template v-slot:activator>
            <v-list-item-content>
              <v-list-item-title><v-icon color="pink lighten-3">favorite</v-icon></v-list-item-title>
            </v-list-item-content>
          </template>
          <v-list-item style="padding-left:20px;">
            <div id="heart" draggable="true" @dragstart="dragStart">
              <svg xmlns="http://www.w3.org/2000/svg" style="border: medium solid #ffffff;" width="70" height="70" viewbox="0 0 100 70">
                <path d="M30 15 a10,10 90 0,1 20,20 l -20 20 -20 -20 a10,10 90 0,1 20,-20 z" fill="#fe65b7" />
              </svg>
            </div>
            <div id="circle" draggable="true" @dragstart="dragStart">
              <svg xmlns="http://www.w3.org/2000/svg" style="border: medium solid #ffffff;" width="70" height="70" viewbox="0 0 100 70">
                <circle cx=30 cy=28 r=23 fill="#e9c904"/>
              </svg>
            </div>
            <div id="square" draggable="true" @dragstart="dragStart">
              <svg xmlns="http://www.w3.org/2000/svg" style="border: medium solid #ffffff;" width="70" height="70" viewbox="0 0 100 70">
                <rect x="10" y="6" rx="0" ry="0" width="45" height="45" stroke-width="1" stroke="none" fill="#8fc33a"/>
              </svg>
            </div>
          </v-list-item>
          <v-list-item style="padding-left:0px;">
            <svg xmlns="http://www.w3.org/2000/svg" style="border: medium solid #ffffff;" width="300" height="70" viewbox="100 0 300 100">
              <polygon points="25 50, 50 6, 75 50" stroke-width="1" stroke="none" fill="#fe65b7"/>
              <path  d="
                M 120.000 45.000
                L 137.634 54.271
                L 134.266 34.635
                L 148.532 20.729
                L 128.817 17.865
                L 120.000 0.000
                L 111.183 17.865
                L 91.468 20.729
                L 105.734 34.635
                L 102.366 54.271
                L 120.000 45.000
                "  fill="#e9c904"/>
              <polygon points="170 30, 195 6, 220 30, 195 54" stroke-width="1" stroke="none" fill="#8fc33a"/>
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
            <svg xmlns="http://www.w3.org/2000/svg" style="border: medium solid #ffffff;" width="300" height="100" viewbox="100 0 300 100">
              <circle cx=50 cy=50 r=40 fill="blue"/>
              <rect x="100" y="14" rx="0" ry="0" width="75" height="75" stroke-width="1" stroke="blue" fill="blue"/>
            </svg>
          </v-list-item>
          <v-list-item style="padding-left:0px;">
            <svg xmlns="http://www.w3.org/2000/svg" style="border: medium solid #ffffff;" width="300" height="100" viewbox="100 0 300 100">
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
            <svg xmlns="http://www.w3.org/2000/svg" style="border: medium solid #ffffff;" width="300" height="100" viewbox="100 0 300 100">
              <circle cx=50 cy=50 r=40 fill="blue"/>
              <rect x="100" y="14" rx="0" ry="0" width="75" height="75" stroke-width="1" stroke="blue" fill="blue"/>
            </svg>
          </v-list-item>
          <v-list-item style="padding-left:0px;">
            <svg xmlns="http://www.w3.org/2000/svg" style="border: medium solid #ffffff;" width="300" height="100" viewbox="100 0 300 100">
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

    <v-content>
      <v-container style="background-color:#ec407a; margin:0 0 0 0; height:56px; max-width: none;">
        <v-row style="margin: auto; max-width:960px;">
          <v-toolbar-title class="white--text">Icon Generator</v-toolbar-title>
        </v-row>
      </v-container>
      <v-container>
        <nuxt />
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
      drawer: true,
      year: 2020,
      mini: true
    }),
    mounted () {
      const today = new Date()
      this.year = today.getFullYear()
    },
    methods: {
      dragStart() {
        console.log(event.target.id)
        event.dataTransfer.setData("text", event.target.id);
      }
    }
  }
</script>