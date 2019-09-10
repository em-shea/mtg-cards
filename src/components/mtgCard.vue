<template>
  <div class="card p-2 m-1">
    <img v-if="card.image_uris" :src="card.image_uris.normal" :class="{ 'split-layout' : card.layout === 'split'}" class="card-img-top" alt="card.name">
    <img v-else-if="card.card_faces" :src="card.card_faces[0].image_uris.normal" class="card-img-top" alt="card.name">
    <div class="card-body">
      <p class="card-text">{{ card.name }}</p>
      <!-- <p v-if="card.oracle_text" class="card-text">{{ card.oracle_text }}</p>
      <p v-else-if="card.card_faces" class="card-text">{{ card.card_faces[0].oracle_text }}</p> -->
    </div>
  </div>
</template>

<script>
export default {
  name: 'mtgCard',
  props: {
    card: Object
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
