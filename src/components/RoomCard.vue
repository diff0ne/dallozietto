<template>
  <v-card class="room-card" elevation="2">
    <v-img :src="room.image" aspect-ratio="1.5"></v-img>
    <v-card-title>{{ room.name }}</v-card-title>
    <v-card-subtitle>{{ room.location }}</v-card-subtitle>
    <v-card-actions>
      <!-- Open the dialog on button click -->
      <v-btn text color="primary" @click="openDialog">View Details</v-btn>
    </v-card-actions>

    <!-- Dialog component for room details -->
    <v-dialog v-model="dialog" max-width="500">
      <v-card>
        <v-card-title>{{ room.name }}</v-card-title>
        <v-card-text>
          <p>Location: {{ room.location }}</p>
          <p>Dimension: {{ room.dimension }}</p>
          <p>People Allowed: {{ room.maxCapacity }}</p>
          <p>Services: {{ room.services }}</p>
        </v-card-text>
        <v-card-actions>
          <!-- Close the dialog -->
          <v-btn text @click="closeDialog">Close</v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
  </v-card>
</template>

<script>
export default {
  name: "RoomCard",
  props: {
    room: {
      type: Object,
      required: true,
    },
  },
  data() {
    return {
      dialog: false, // Dialog state
    };
  },
  methods: {
    openDialog() {
      this.dialog = true; // Open the dialog
    },
    closeDialog() {
      this.dialog = false; // Close the dialog
    },
  },
};
</script>

<style scoped>
.room-card {
  margin: 20px;
}
</style>
