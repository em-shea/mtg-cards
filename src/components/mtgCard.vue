<template>
  <div v-if="card.image_uris" class="card p-2 m-1" v-on:click="clickCard()">
    <img :src="card.image_uris.normal" :class="[ card.layout, card.set, { 'is-clicked' : clicked }]" class="card-img-top" :alt="card.name">
    <div class="card-body">
      <p class="card-text">{{ card.name }}</p>
    </div>
  </div>

  <div v-else-if="card.card_faces" class="card multi-face-card p-2 m-1" v-on:click="transformCard()">
    <img :src="card.card_faces[0].image_uris.normal" class="card-img-top" v-show="!transformed" :alt="card.name">
    <img :src="card.card_faces[1].image_uris.normal" class="card-img-top" v-show="transformed" :alt="card.name">
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
      transformed: false,
      clicked: false
    }
  },
  methods: {
    transformCard () {
      console.log('transforming', this.transformed)
      if (this.transformed === false) {
        this.transformed = true
      } else {
        this.transformed = false
      }
    },
    clickCard () {
      console.log('clicking', this.clicked)
      if (this.clicked === false) {
        this.clicked = true
      } else {
        this.clicked = false
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .card img {
    transition: all 0.5s;
  }
  .multi-face-card img:hover {
    cursor: pointer;
  }
  img.flip.is-clicked {
    transform: scale(1) rotate(180deg);
  }
  /* img.split.is-clicked,
  img.planar.is-clicked {
    transform: scale(1) rotate(90deg);
  }
  img.split.c19.is-clicked,
  img.split.hou.is-clicked,
  img.split.akh.is-clicked {
    transform: scale(1) rotate(-90deg);
  } */
  @media screen and (min-width: 800px) {
    .card img:hover {
      transform: scale(2) rotate(0deg);
      z-index: 2;
    }
    img.flip.is-clicked:hover {
      cursor: pointer;
      transform: scale(2) rotate(180deg);
    }
    img.split:hover,
    img.planar:hover {
      transform: scale(2) rotate(90deg);
      z-index: 2;
    }
    img.split.is-clicked:hover,
    img.planar.is-clicked:hover {
      transform: scale(2) rotate(90deg);
      z-index: 2;
    }
    img.split.is-clicked,
    img.planar.is-clicked {
      transform: scale(1) rotate(0deg);
    }
    img.split.c19.is-clicked,
    img.split.hou.is-clicked,
    img.split.akh.is-clicked {
      cursor: pointer;
      transform: scale(1) rotate(0deg);
    }
    img.split.c19:hover,
    img.split.hou:hover,
    img.split.akh:hover {
      cursor: pointer;
      transform: scale(2) rotate(0deg);
      transition: all 0.5s;
      z-index: 2;
    }
    img.split.c19.is-clicked:hover,
    img.split.hou.is-clicked:hover,
    img.split.akh.is-clicked:hover {
      cursor: pointer;
      transform: scale(2) rotate(-90deg);
      z-index: 2;
    }
  }
</style>
