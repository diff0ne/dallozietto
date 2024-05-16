<template>
  <div class="main-content">
    <div class="propic-container">
      <img class="propic" src="@/assets/propic.png" alt="Propic" />
    </div>
    <div class="introduction">
      <div class="divider"></div>
      <h2 class="display-2 text-center bilbo-regular">La mia casa - Amabel</h2>
      <p class="text-center w-auto">
        Benvenuti nella mia villa nel verde! Mi chiamano lo
        <span style="font-style: italic; color: green">Zietto</span> e sono un
        appassionato della natura e della campagna. <br />
        Qui, tra gli alberi e il canto degli uccelli, ho creato un rifugio
        accogliente per chi cerca pace e tranquillità. <br />
        Siate i benvenuti a condividere con me questo angolo di paradiso.
      </p>
    </div>
    <v-carousel cycle hide-delimiter-background class="small-carousel">
      <v-carousel-item v-for="(image, index) in carouselImages" :key="index">
        <div class="carousel-item">
          <img :src="image" class="carousel-image" />
        </div>
      </v-carousel-item>
    </v-carousel>
    <div class="divider pt-10"></div>
    <h2 class="display-2 text-center bilbo-regular">Le mie stanze</h2>
    <div class="featured-rooms">
      <v-container fluid>
        <v-row>
          <v-col
            v-for="(room, index) in featuredRooms"
            :key="index"
            cols="12"
            sm="6"
            md="6"
            class="room-center"
          >
            <RoomCard :room="room" :imageSrc="room.imageSrc" />
          </v-col>
        </v-row>
      </v-container>
    </div>
    <div class="divider pt-10"></div>
    <h2 class="display-2 text-center bilbo-regular">Servizi</h2>
    <Services />
    <div class="divider pt-10"></div>
    <h2 class="display-2 text-center bilbo-regular">Regolamento</h2>
    <Rules />
  </div>
</template>

<script>
import RoomCard from "@/components/RoomCard.vue";

export default {
  name: "MainContent",
  components: {
    RoomCard,
  },
  props: {
    featuredRooms: {
      type: Array,
      required: true,
    },
  },
  data() {
    return {
      carouselImages: [
        "src/assets/overView/image1.jpeg",
        "src/assets/overView/image2.jpeg",
        "src/assets/overView/image3.jpeg",
        "src/assets/overView/image4.jpeg",
        "src/assets/overView/image5.jpeg",
        "src/assets/overView/image6.jpeg",
      ],
    };
  },
  methods: {
    async getRoomImageSrc(roomName) {
      try {
        const image = await import(
          `@/assets/${roomName.toLowerCase()}/main.jpg`
        );
        console.log("Image path:", image.default);
        return image.default;
      } catch (error) {
        console.error(`Error loading image for room ${roomName}:`, error);
        return "";
      }
    },
  },
  async created() {
    const updatedRooms = await Promise.all(
      this.featuredRooms.map(async (room) => {
        room.imageSrc = await this.getRoomImageSrc(room.name);
        return room;
      })
    );
    this.featuredRooms = updatedRooms;
  },
};
</script>

<style scoped>
.room-center {
  display: flex;
  justify-content: center;
}

.main-content {
  position: relative;
}
.propic-container {
  height: 18vh;
  background-color: #182524;
  background-size: cover;
  background-position: center;
  width: 100%;
}
.propic {
  display: block;
  margin: auto;
  height: 100%;
  width: auto;
}
.introduction {
  padding: 20px;
  text-align: center;
}
.small-carousel {
  height: 55vh !important;
  margin: auto;
}
.carousel-item {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100%;
}
.carousel-image {
  max-width: 100%;
  max-height: 100%;
  box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.5);
  transition: box-shadow 0.3s;
  border-radius: 2%;
}
.carousel-image:hover {
  box-shadow: 0px 0px 20px rgba(0, 0, 0, 0.4);
}
.divider {
  width: 50%;
  margin: auto;
  border-bottom: 2px solid #182524;
  margin-bottom: 10px;
}
</style>
