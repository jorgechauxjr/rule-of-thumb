<script setup>
import CardMain from './CardMain.vue'
import info from '@/assets/data.json'
import im1 from '../assets/img/kanye.png'
import im2 from '../assets/img/mark.png'
import im3 from '../assets/img/cristina.png'
import im4 from '../assets/img/malala.png'
import im5 from '../assets/img/elon.png'
import im6 from '../assets/img/greta.png'

const images = [im1, im2, im3, im4, im5, im6]

const persons = info.data
</script>
<template>
  <div class="container">
    <div class="row">
      <div class="col-md-4" v-for="(person, index) in persons" :key="index">
        <CardMain
          :name="person.name"
          :picture="images[index]"
          :description="person.description"
          :category="person.category"
          :last-updated="person.lastUpdated"
          :positive-votes="person.votes.positive"
          :negative-votes="person.votes.negative"
        />
      </div>
    </div>
  </div>
</template>
