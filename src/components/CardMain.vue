<script setup>
import thumbsUp from '@/assets/img/thumbs-up.svg'
import thumbsDown from '@/assets/img/thumbs-down.svg'

const props = defineProps({
  picture: String,
  name: String,
  description: String,
  category: String,
  lastUpdated: String,
})
console.log('Name: ', props.name)
</script>

<template>
  <div class="card">
    <div class="card-body">
      <img :src="picture" alt="" class="img-fluid" />
      <img src="" alt="" />
      <h4 class="card-title">{{ name }}</h4>
      <p class="card-text">{{ description }}</p>
      <p>Last updated: {{ lastUpdated }} in {{ category }}</p>
      <button class="btn btn-success">
        <img :src="thumbsUp" alt="thumbs up" />
      </button>
      <button class="btn btn-danger">
        <img :src="thumbsDown" alt="thumbs down" />
      </button>
      <button class="btn btn-light">VOTE NOW</button>
    </div>
  </div>
</template>
