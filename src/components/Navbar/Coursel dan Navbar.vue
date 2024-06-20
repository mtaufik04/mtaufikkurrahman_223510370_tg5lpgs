<template>
  <div>
    <q-layout view="hHh lpR fFf">
      <!-- Header -->
      <q-header elevated class="bg-gradient-to-r from-teal-400 to-blue-500 text-white" :style="{ height: '100px', fontFamily: 'Arial, sans-serif' }">
        <div class="toolbar">
          <q-toolbar-title align="left" style="font-family: 'Pacifico', cursive; font-size: 1.8rem;">
            TOKO JAM ONLINE
          </q-toolbar-title>
          <div class="search-input">
            <q-input filled v-model="text" label="Cari produk...">
              <template v-slot:prepend>
                <q-icon name="search" />
              </template>
              <template v-slot:append v-if="text">
                <q-icon name="close" @click="clearSearch" />
              </template>
            </q-input>
          </div>
          <div class="icons">
            <q-btn flat round icon="shopping_basket" class="icon-btn" />
            <q-btn flat round icon="account_circle" class="icon-btn" />
            <q-btn flat round icon="notifications" class="icon-btn">
              <q-badge floating color="red" rounded />
            </q-btn>
          </div>
        </div>
      </q-header>

      <!-- Page Content -->
      <q-page-container class="q-pa-md">
        <router-view />
        <!-- Carousel -->
        <div class="carousel-wrapper">
          <q-carousel
            animated
            v-model="slide"
            arrows
            navigation-label="..."
            infinite
            :autoplay="autoplay"
            prev-icon="keyboard_arrow_left" 
            next-icon="keyboard_arrow_right" 
            height="400px"
            @mouseenter="autoplay = false"
            @mouseleave="autoplay = true"
          >
            <q-carousel-slide :name="1" img-src="https://1.bp.blogspot.com/-Juxa-znLy58/WtSn9W6tNZI/AAAAAAAAGZg/8MUbT9J1AsUq0_CTPxstaM4kdG43QXRPwCK4BGAYYCw/s1600/banner13.png" />
            <q-carousel-slide :name="2" img-src="https://blog.jamtangan.com/wp-content/uploads/2022/09/jam-tangan-untuk-kulit-sawo-matang.jpg" />
            <q-carousel-slide :name="3" img-src="https://blog.jamtangan.com/wp-content/uploads/2022/08/Cover-Blog-16-agustus-jam-tangan-pria-mahal.jpg" />
            <q-carousel-slide :name="4" img-src="https://s3.cosmopolitan.co.id/OPJam-Tangan-Cowo_60_20190224142449ISPNZQ.jpg" />
            <q-carousel-slide :name="5" img-src="https://static.vecteezy.com/system/resources/previews/000/176/229/original/vector-grand-offer-sale-and-discount-banner-template-for-promotion.jpg" />
          </q-carousel>
        </div>
      </q-page-container>
    </q-layout>
  </div>
</template>

<script>
import { ref } from 'vue';

export default {
  setup() {
    const slide = ref(1);
    const text = ref('');
    const autoplay = ref(true);

    const clearSearch = () => {
      text.value = '';
    };

    return {
      slide,
      text,
      clearSearch,
      autoplay,
    };
  },
};
</script>

<style scoped>
.toolbar {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0 20px;
}

.search-input {
  flex-grow: 1;
  margin-left: 20px;
}

.icons {
  display: flex;
  gap: 15px;
}

.icon-btn {
  font-size: 24px;
  color: white;
}

.carousel-wrapper {
  margin-top: 20px;
}

.q-carousel-slide img {
  height: 400px;
  object-fit: cover;
  border-radius: 10px;
  transition: transform 0.3s ease;
}

.q-carousel-slide:hover {
  transform: scale(1.05);
}
</style>
