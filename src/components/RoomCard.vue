<template>
  <v-card @click="openDialog" class="room-card" elevation="1">
    <v-img :src="imageSrc" aspect-ratio="1.5"></v-img>
    <v-card-title>{{ capitalizeFirstLetter(room.name) }}</v-card-title>
    <v-card-text>
      <p>Numero Ospiti: {{ room.maxCapacity }}</p>
      <p>{{ room.description }}</p>
    </v-card-text>
    <v-card-actions>
      <!-- Open the dialog on button click -->
      <v-btn text color="primary" @click="openDialog">View Details</v-btn>
    </v-card-actions>

    <!-- Dialog component for room details -->
    <v-dialog v-model="dialog">
      <v-card>
        <v-card-title>{{ capitalizeFirstLetter(room.name) }}</v-card-title>
        <v-card-text>
          <p>{{ room.description }}</p>
          <p>People Allowed: {{ room.maxCapacity }}</p>
          <p>Dimension: {{ room.dimension }}</p>
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
      dialog: false,
    };
  },
  methods: {
    openDialog() {
      this.dialog = true; // Open the dialog
    },
    closeDialog() {
      this.dialog = false; // Close the dialog
    },
    capitalizeFirstLetter(text) {
      return text.charAt(0).toUpperCase() + text.slice(1);
    },
  },
};
</script>

<style scoped></style>
