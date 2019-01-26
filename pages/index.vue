<template>
  <v-layout
    column
    justify-center
    align-center
  >
    <v-flex
      xs12
      sm8
      md6
    >
      
      <v-card>
        <v-card-title class="headline">Welcome to the Vuetify + Nuxt.js template</v-card-title>
        <v-card-text>
          <p>Vuetify is a progressive Material Design component framework for Vue.js. It was designed to empower developers to create amazing applications.</p>
          <p>For more information on Vuetify, check out the <a
            href="https://vuetifyjs.com"
            target="_blank"
          >documentation</a>.</p>
          <div class="text-xs-right">
            <em><small>&mdash; John Leider</small></em>
          </div>
        </v-card-text>
      </v-card>

      <div class="text-xs-center">
        <v-dialog
          v-model="dialog"
          width="500"
        >
          <!-- <v-btn
            slot="activator"
            color="red lighten-2"
          >
            button
          </v-btn> -->


          <div 
            slot="activator"
            @click="clickImg"
          >
            <v-img
              src="/gif/3.gif"
            ></v-img>
          </div>

          <v-card>
            <v-card-title
              class="headline grey lighten-2"
              primary-title
            >
              {{ name }}
            </v-card-title>

            <v-card-text>
              Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.
            </v-card-text>

            <v-divider></v-divider>

            <v-card-actions>
              <v-spacer></v-spacer>
              <v-btn
                color="primary"
                flat
                @click="dialog = false"
              >
                I accept
              </v-btn>
            </v-card-actions>
          </v-card>
        </v-dialog>
      </div>
    </v-flex>
  </v-layout>
</template>

<script>
import Logo from '~/components/Logo.vue'

export default {
  components: {
    Logo,
  },
  data () {
    return {
      dialog: false,
      name: 'jj'
    }
  },
  methods:{
    clickImg(){
      var random = require('random-name')
      this.name = random()
      this.dialog = false
      console.log("hihi")
    }
  }
}
</script>
