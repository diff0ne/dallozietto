<template>
    <v-card class="room-card" elevation="2">
      <v-img :src="room.image" aspect-ratio="1.5"></v-img>
      <v-card-title>{{ room.name }}</v-card-title>
      <v-card-subtitle>{{ room.location }}</v-card-subtitle>
      <v-card-actions>
        <v-btn text color="primary">View Details</v-btn>
      </v-card-actions>
    </v-card>
  </template>
  
  <script>
  export default {
    name: 'RoomCard',
    props: {
      room: {
        type: Object,
        required: true
      }
    }
  }
  </script>
  
  <style scoped>
  .room-card {
    margin: 20px;
  }
  </style>
  