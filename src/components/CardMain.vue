<script setup>
import { ref } from 'vue'
import thumbsUp from '@/assets/img/thumbs-up.svg'
import thumbsDown from '@/assets/img/thumbs-down.svg'

defineProps({
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

function selectVote(thumbsType) {
  selectedVote.value = thumbsType
  enableVote()
}

function enableVote() {
  if (voteIsActive.value === false) {
    voteIsActive.value = true
    voteNow.value = 'btn btn-light'
  }
  console.log('Activo?-> ', voteIsActive.value)
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
      <button :class="voteNow">VOTE NOW</button>
    </div>
    <p>{{ positiveVotes }}</p>
    <p>{{ negativeVotes }}</p>
  </div>
</template>
