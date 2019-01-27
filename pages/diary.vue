<template>
  <div>
    <v-select v-bind:items="items" v-model="selected" label="Select a language"></v-select>
    <v-btn color="info" @click="onSummit">Summit</v-btn>

    <v-dialog
      v-model="dialog1"
      width="800"
    >
      <v-btn
        slot="activator"
        color="red lighten-2"
        dark
      >
        Demo1
      </v-btn>

      <v-card>
          <v-img
            class="white--text"
            height="200px"
            src="/gif/8.gif"
            >
            <v-container fill-height fluid>
                <v-layout fill-height>
                <v-flex xs12 align-end flexbox>
                    <span class="headline"></span>
                </v-flex>
                </v-layout>
            </v-container>
          </v-img>
        <v-card-title
          class="headline grey lighten-2"
          primary-title
        >
          Report    
        </v-card-title>

        <v-card-text>
            <p class="headline">我今日食左碗牛肉麵，好彈牙，下次一定會再黎食。之後去咗公園睇人捉棋。最後返屋企，我現時自己肯做飯。</p>
            <p class="title">Sentimemt Analysis</p>
            <v-progress-linear
                color="success"
                height="20"
                value="86.12321019172668"
            ></v-progress-linear>

            <div class="headline">Summary</div>
            <p class="subheading">我今日食左碗牛肉麵，好彈牙，下次一定會再黎食。</p>

            <div class="headline">Root Topics</div>
            <v-chip label color="blue" text-color="white">
                <v-icon left>label</v-icon>飲食
            </v-chip>
            <br>
            <div class="headline">Related Topics</div>
            <v-chip label color="pink" text-color="white">
                <v-icon left>label</v-icon>美食餐飲
            </v-chip>
            <v-chip label color="pink" text-color="white">
                <v-icon left>label</v-icon>勞碌
            </v-chip>
            <v-chip label color="pink" text-color="white">
                <v-icon left>label</v-icon>休閒設施
            </v-chip>

        </v-card-text>

        <v-divider></v-divider>

        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn
            color="primary"
            flat
            @click="dialog1 = false"
          >
          <router-link to="/" tag="button">
            Summit
          </router-link>
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>

    <br>
    <vue-speech 
        v-show="recording"
        :lang="selected"
        @onTranscriptionEnd="onEnd"
    />
  </div>
</template>

<script>
import Vue from 'vue'
import VueSpeech from 'vue-speech'
import axios from 'axios'


Vue.use(VueSpeech)

export default {
    data(){
        return {
            dialog1: false,
            recording: true,
            selected: 'yue-Hant-HK',
            transcription: [],
            final_transcription: '',
            items: [{
                text: 'Afrikaans (Suid-Afrika)',
                value: 'af-ZA'
            },
            {
                text: 'Deutsch (Deutschland)',
                value: 'de-DE'
            },
            {
                text: 'English (United States)',
                value: 'en-US'
            },
            {
                text: 'Français (France)',
                value: 'fr-FR'
            },
            {
                text: '한국어 (대한민국)',
                value: 'ko-KR'
            },
            {
                text: '國語 (台灣)',
                value: 'cmn-Hant-TW'
            },
            {
                text: '廣東話 (香港)',
                value: 'yue-Hant-HK'
            },
            {
                text: '日本語（日本)',
                value: 'ja-JP'
            },
            {
                text: '普通話 (香港)',
                value: 'cmn-Hans-HK'
            },
            {
                text: '普通话 (中国大陆)',
                value: 'cmn-Hans-CN'
            }
            ]
        }
    },
    methods: {
        onEnd ({ lastSentence, transcription }) {
            // `lastSentence` is the last sentence before the pause
            // `transcription` is the full array of sentences
            console.log("lastSentence: " + lastSentence);
            console.log("transcription: " + transcription.join(' '))
            this.transcription = transcription
        },
        onSummit(){

            axios.post('http://ailab-test-api-lb.wisers.com/senti/sentiment/document', {
                text: '我今日好開心'
            })
            .then(function (response) {
                console.log(response);
                console.log('hihi')
            })
            .catch(function (error) {
                console.log(error);
            });
            
        }
    }
}
</script>

<style lang="css">
</style>