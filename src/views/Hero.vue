<template>
  <v-parallax
    dark
    src="https://cdn.vuetifyjs.com/images/backgrounds/vbanner.jpg"
  >
    <v-row
      align="center"
      justify="center"
    >
      <v-col
        class="text-center"
        cols="08"
      >
        <h1 class="display-1 font-weight-thin mb-4">
          
        </h1>
        <h4 class="subheading">
            
          Vue-To-Do List Maker
        </h4>
        <v-menu
      v-model="menu"
      :close-on-content-click="false"
      :nudge-width="200"
      offset-x
    >
      <template v-slot:activator="{ on, attrs }">
        <v-btn
          color="indigo"
          dark
          v-bind="attrs"
          v-on="on"
        >
          app by
        </v-btn>
      </template>

      <v-card>
        <v-list>
          <v-list-item>
            <v-list-item-avatar>
              <img
                src="https://cdn.vuetifyjs.com/images/john.jpg"
                alt="John"
              >
            </v-list-item-avatar>

            <v-list-item-content>
              <v-list-item-title>Hayden MacDonald</v-list-item-title>
              <v-list-item-subtitle>websuitestudio.com</v-list-item-subtitle>
            </v-list-item-content>

            <v-list-item-action>
              <v-btn
                :class="fav ? 'red--text' : ''"
                icon
                @click="fav = !fav"
              >
                <v-icon>mdi-pencil-circle</v-icon>
              </v-btn>
            </v-list-item-action>
          </v-list-item>
        </v-list>

        <v-divider></v-divider>

    
        <v-card-actions>
          <v-spacer></v-spacer>

          
          <v-btn
            color="primary"
            text
            outlined
            @click="menu = false"
          >
            Save
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-menu>
      </v-col>
    </v-row>
  </v-parallax> 
</template>
