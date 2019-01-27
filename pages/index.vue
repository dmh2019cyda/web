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
        <v-card-title class="headline">Welcome to CYDA Community!</v-card-title>
        <v-card-text>
          
          <p>Take some time to look out of the window, feel the blue sky and the fresh air.</p>
          <p>Now share with me anything that come into your mind. What have you eaten? How was your day? I am excited to know it!</p>
          <div class="text-xs-right">
            <em><small>&mdash; CYDA</small></em>
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
              {{ name }} ({{ place }})
            </v-card-title>

            <v-card-text>
              <div class="text-xs-center">
                <v-chip>
                  <v-avatar>
                    <img src="/badge/1.png">
                  </v-avatar>
                  11
                </v-chip>
                <v-chip>
                  <v-avatar>
                    <img src="/badge/2.png">
                  </v-avatar>
                  11
                </v-chip>
                <v-chip>
                  <v-avatar>
                    <img src="/badge/3.png">
                  </v-avatar>
                  11
                </v-chip>
                <v-chip>
                  <v-avatar>
                    <img src="/badge/4.png">
                  </v-avatar>
                  11
                </v-chip>
                <v-chip>
                  <v-avatar>
                    <img src="/badge/5.png">
                  </v-avatar>
                  11
                </v-chip>
                <v-chip>
                  <v-avatar>
                    <img src="/badge/6.png">
                  </v-avatar>
                  11
                </v-chip>
              </div>
            </v-card-text>



            <v-divider></v-divider>

            <v-card-actions>
              <v-spacer></v-spacer>
              <v-btn
                color="primary"
                flat
                @click="dialog = false"
              >
                Close
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
      name: 'jj',
      placeid: 0,
      place: '',
      places: [
        'Central and Western',
        'Eastern',
        'Southern',
        'Wan Chai',
        'Sham Shui Po',
        'Kowloon City',
        'Kwun Tong',
        'Wong Tai Sin',
        'Yau Tsim Mong',
        'Islands',
        'Kwai Tsing',
        'North',
        'Sai Kung',
        'Sha Tin',
        'Tai Po',
        'Tsuen Wan',
        'Tuen Mun',
        'Yuen Long',
      ]
    }
  },
  methods:{
    clickImg(){
      var random = require('random-name')
      this.name = random.first()
      this.place = this.places[Math.floor(Math.random() * Math.floor(18))];
      this.dialog = true
    }
  }
}
</script>
