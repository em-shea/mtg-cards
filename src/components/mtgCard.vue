<template>
  <div v-if="card.image_uris" class="card p-2 m-1">
    <img :src="card.image_uris.normal" :class="{ 'split-layout' : card.layout === 'split' }" class="card-img-top" :alt="card.name">
    <div class="card-body">
      <p class="card-text">{{ card.name }}</p>
    </div>
  </div>
  <div v-else-if="card.card_faces" class="card multi-face-card p-2 m-1" v-on:click="flipCard()">
    <img :src="card.card_faces[0].image_uris.normal" class="card-img-top" v-show="!flipped" :alt="card.name">
    <img :src="card.card_faces[1].image_uris.normal" class="card-img-top" v-show="flipped" :alt="card.name">
    <div class="card-body">
      <p class="card-text">{{ card.name }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'mtgCard',
  props: {
    card: Object
  },
  data () {
    return {
      flipped: false
    }
  },
  methods: {
    flipCard () {
      console.log('flipping', this.flipped)
      if (this.flipped === false) {
        this.flipped = true
      } else {
        this.flipped = false
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .card img:hover {
    transform: none;
  }
  @media screen and (min-width: 800px) {
    .card img:hover {
      transform: scale(2);
      transition: all 0.5s;
      z-index: 2;
    }
  }
  .single-card {
    padding-top: 30px;
  }
  img.split-layout:hover {
    transform: scale(2) translate(0, 0) rotate(90deg);
    z-index: 2;
  }

  .multi-face-card img:hover {
    cursor: pointer;
  }
</style>
