<script setup>
import { ref } from 'vue'
import thumbsUp from '@/assets/img/thumbs-up.svg'
import thumbsDown from '@/assets/img/thumbs-down.svg'

const props = defineProps({
  picture: String,
  name: String,
  description: String,
  category: String,
  lastUpdated: String,
  positiveVotes: Number,
  negativeVotes: Number,
})
const selectedVote = ref(null)
const voteIsActive = ref(false)
const voteNow = ref('btn btn-light disabled')
const positive = ref(props.positiveVotes)
const negative = ref(props.negativeVotes)

function selectVote(thumbsType) {
  selectedVote.value = thumbsType
  console.log('TIPO de voto ', selectedVote.value)
  enableVote()
}

function enableVote() {
  if (voteIsActive.value === false) {
    voteIsActive.value = true
    voteNow.value = 'btn btn-light'
  }
  console.log('Activo?-> ', voteIsActive.value)
}

function handleVoteNow() {
  console.log('POSITIVOS: ', positive.value)
  console.log('manito: ', selectedVote.value)
  if (selectedVote.value == 'up') {
    positive.value = positive.value + 1
  } else {
    if (selectedVote.value == 'down') {
      negative.value = negative.value + 1
    }
  }
  console.log('votos P ', positive.value)
}
</script>

<template>
  <div class="card">
    <div class="card-body">
      <img :src="picture" alt="" class="img-fluid" />
      <img src="" alt="" />
      <h4 class="card-title">{{ name }}</h4>
      <p class="card-text">{{ description }}</p>
      <p>Last updated: {{ lastUpdated }} in {{ category }}</p>
      <button class="btn btn-success" @click="selectVote('up')">
        <img :src="thumbsUp" alt="thumbs up" />
      </button>
      <button class="btn btn-danger" @click="selectVote('down')">
        <img :src="thumbsDown" alt="thumbs down" />
      </button>
      <button :class="voteNow" @click="handleVoteNow()">VOTE NOW</button>
    </div>
    <p>{{ positive }}</p>
    <p>{{ negative }}</p>
  </div>
</template>
