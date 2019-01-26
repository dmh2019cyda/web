<template>
  <div>
    <v-select v-bind:items="items" v-model="selected" label="Select a language"></v-select>
    <v-btn 
        v-show="!recording"
        color="success"
        @click="start"
    >
        Start Recording
    </v-btn>
    <v-btn 
        v-show="recording"
        color="warning"
        @click="end"
    >
        Stop Recording
    </v-btn>
    <v-btn color="info" @onTranscriptionEnd="onSummit">Summit</v-btn>
    <vue-speech 
        v-show="recording"
        :lang="selected"
        @onTranscriptionEnd="onEnd"
    />
    <br>
    <p v-show="!recording">{{ final_transcription }}</p>
    
  </div>
</template>

<script>
import Vue from 'vue'
import VueSpeech from 'vue-speech'


Vue.use(VueSpeech)

export default {
    data(){
        return {
            recording: false,
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
        start(){
            this.recording = true
            console.log(this.recording)
            this.transcription = []
            this.final_transcription = ''
        },
        end(){
            this.recording = false
            console.log(this.recording)
            this.final_transcription = this.transcription.join(' ')
        },
        onSummit(){
            
        }
    }
}
</script>

<style lang="css">
</style>