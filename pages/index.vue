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
          <v-card>
            <v-card-title
              class="headline grey lighten-2"
              primary-title
            >
              {{ name }}
            </v-card-title>

            <v-card-text>
              <v-layout>
                <div v-if="Math.random() > 0.5">
                  <v-img
                    src="/badge/1.png"
                    height="50px"
                    width="50px"
                    contain="true"
                  ></v-img>
                </div>
                <div v-else>
                  <v-img
                    src="/badge/locked.png"
                    height="50px"
                    width="50px"
                    contain="true"
                  ></v-img>
                </div>
                <div v-if="Math.random() > 0.5">
                  <v-img
                    src="/badge/2.png"
                    height="50px"
                    width="50px"
                    contain="true"
                  ></v-img>
                </div>
                <div v-else>
                  <v-img
                    src="/badge/locked.png"
                    height="50px"
                    width="50px"
                    contain="true"
                  ></v-img>
                </div><div v-if="Math.random() > 0.5">
                  <v-img
                    src="/badge/3.png"
                    height="50px"
                    width="50px"
                    contain="true"
                  ></v-img>
                </div>
                <div v-else>
                  <v-img
                    src="/badge/locked.png"
                    height="50px"
                    width="50px"
                    contain="true"
                  ></v-img>
                </div><div v-if="Math.random() > 0.5">
                  <v-img
                    src="/badge/4.png"
                    height="50px"
                    width="50px"
                    contain="true"
                  ></v-img>
                </div>
                <div v-else>
                  <v-img
                    src="/badge/locked.png"
                    height="50px"
                    width="50px"
                    contain="true"
                  ></v-img>
                </div><div v-if="Math.random() > 0.5">
                  <v-img
                    src="/badge/5.png"
                    height="50px"
                    width="50px"
                    contain="true"
                  ></v-img>
                </div>
                <div v-else>
                  <v-img
                    src="/badge/locked.png"
                    height="50px"
                    width="50px"
                    contain="true"
                  ></v-img>
                </div><div v-if="Math.random() > 0.5">
                  <v-img
                    src="/badge/6.png"
                    height="50px"
                    width="50px"
                    contain="true"
                  ></v-img>
                </div>
                <div v-else>
                  <v-img
                    src="/badge/locked.png"
                    height="50px"
                    width="50px"
                    contain="true"
                  ></v-img>
                </div>
              </v-layout>
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

        <v-img
          @click="clickImg"
          src="/gif/3.gif"
        ></v-img>
        
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
      this.dialog = true
    }
  }
}
</script>
