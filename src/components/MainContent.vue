<template>
    <div class="main-content">
      <div class="hero">
        <h2 class="display-2 text-center font-title">
            Benvenuto dallo Zietto
        </h2>
        <p class="text-center w-auto">
          Benvenuti nella casa dello Zietto! Siamo entusiasti di potervi
          offrire un'esperienza unica e accogliente. Qui troverete un
          ambiente caloroso e confortevole, pronto a farvi sentire come a
          casa vostra. Siamo ansiosi di condividere con voi momenti
          indimenticabili e di rendere il vostro soggiorno speciale in ogni
          modo possibile.
        </p>
      </div>
      <div class="featured-rooms">
        <v-row justify="center">
          <v-col
            cols="12"
            sm="6"
            md="4"
            v-for="(room, index) in featuredRooms"
            :key="index"
          >
            <RoomCard :room="room" />
          </v-col>
        </v-row>
      </div>
    </div>
  </template>
  
  <script>
  import RoomCard from '@/components/RoomCard.vue';
  export default {
    name: 'MainContent',
    components: {
      RoomCard
    },
    props: {
      featuredRooms: {
        type: Array,
        required: true
      }
    }
  }
  </script>
  
  <style scoped>
  .main-content {
    background-color: #182524;
    padding: 20px;
  }
  
  .hero {
    margin-bottom: 40px;
  }
  
  .featured-rooms {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
  }
  </style>
  