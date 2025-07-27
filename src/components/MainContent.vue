<template>
  <div class="main-content">
    <div class="propic-container">
      <img class="propic" src="@/assets/propic.jpg" alt="Propic" />
    </div>
    <div class="introduction">
      <div class="divider"></div>
      <h2 class="display-2 text-center bilbo-regular">La mia casa - Amabel</h2>
      <p class="text-center w-auto ">
        Benvenuti a Viganò, nel cuore verde della Brianza.
        <br>
        Appartamento al piano terreno di 160 mq, elegante e rustico, situato sulle colline moreniche dell’Alta Brianza a
        400 metri di altezza.
        <br>
        Circondato da un parco privato di 9.000 mq, immerso nella natura del Parco, con accanto un suggestivo bosco di
        querce, betulle, castagni, ciliegi e felci.
        <br>
        Una location ideale per lavoro, vacanze o una fuga romantica in Brianza: tra le province di Milano, Monza,
        Lecco, Como e la vicina Chiasso.

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
          <v-col v-for="(room, index) in featuredRooms" :key="index" cols="12" sm="6" md="6" class="room-center">
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
import Services from "@/components/Services.vue";
import Rules from "@/components/Rules.vue";

export default {
  name: "MainContent",
  components: {
    RoomCard,
    Services,
    Rules,
  },
  props: {
    featuredRooms: {
      type: Array,
      required: true,
    },
  },
  data() {
    return {
      carouselImages: [],
    };
  },
  methods: {
    async getRoomImageSrc(roomName) {
      try {
        const image = await import(
          `@/assets/${roomName.toLowerCase()}/main.jpg`
        );
        return image.default;
      } catch (error) {
        console.error(`Error loading image for room ${roomName}:`, error);
        return "";
      }
    },
  },
  async created() {
  // Load all overview images
  const images = import.meta.glob('@/assets/overView/*.{jpg,jpeg,png}', {
    eager: true,
    import: 'default',
  });

  // Sort so 'esterno...' comes first
  const sortedKeys = Object.keys(images).sort((a, b) => {
    // Push filenames that start with 'esterno' to the beginning
    const aName = a.toLowerCase();
    const bName = b.toLowerCase();
    const aIsEsterno = aName.includes('esterno');
    const bIsEsterno = bName.includes('esterno');

    if (aIsEsterno && !bIsEsterno) return -1;
    if (!aIsEsterno && bIsEsterno) return 1;
    return aName.localeCompare(bName); 
  });

  this.carouselImages = sortedKeys.map((key) => images[key]);

  const updatedRooms = await Promise.all(
    this.featuredRooms.map(async (room) => {
      room.imageSrc = await this.getRoomImageSrc(room.name);
      return room;
    })
  );
  this.featuredRooms = updatedRooms;
}

};
</script>


<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500&display=swap');

.room-center {
  padding: 16px;
  display: flex;
  justify-content: center;
}

.main-content {
  position: relative;
}

.propic-container {
  height: 20vh;
  background-color: #E6E5D1;
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
  padding: 20px 0;
  text-align: center;

  font-family: 'Poppins', sans-serif;
  font-weight: 300;
  font-size: 1rem;
  line-height: 1.6;
  color: #182524;

}

.small-carousel {
  height: 50vh !important;
  margin: auto;
  width: 50%;
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
  transition: transform 0.5s cubic-bezier(0.4, 0, 0.2, 1), box-shadow 0.5s cubic-bezier(0.4, 0, 0.2, 1);
  padding: 2px;
  border-radius: 4px;
}

.carousel-image:hover {
   transform: scale(1.1);
  box-shadow: 0 0 20px rgba(0, 0, 0, 0.4);
}

.divider {
  width: 50%;
  margin: auto;
  border-bottom: 2px solid #182524;
  margin-bottom: 10px;
}

.featured-rooms {
  width: 90%;
  margin: auto;
  padding-bottom: 38px;
}
</style>
