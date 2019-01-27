<template>
  <div>
    <v-select v-bind:items="items" v-model="selected" label="Select a language"></v-select>
    <v-btn color="info" @click="onSummit">Summit</v-btn>
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


Vue.use(VueSpeech)

export default {
    data(){
        return {
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
            
        }
    }
}
</script>

<style lang="css">
</style>