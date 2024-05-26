<template>
  <div>
    <q-layout view="hHh lpR fFf">
      <q-header elevated class="bg-gradient-to-r from-teal-400 to-blue-500 text-white" :style="{ height: '100px', fontFamily: 'Arial, sans-serif' }">
        <div class="toolbar">
          <q-toolbar-title align="left" style="font-family: 'Pacifico', cursive;">
            TOKO JAM ONLINE
          </q-toolbar-title>
          <div class="search-input">
            <label for="searchInput" class="search-label" :class="{ 'active': text }" @click="focusInput">
              <q-icon name="search" color="white" style="align-items: center;" class="search-icon" />
              {{ text ? '' : '' }}
            </label>
            <input
              id="searchInput"
              v-model="text"
              type="text"
              class="search-textbox"
              placeholder="Hari ini ada diskon besar besaran untuk pengguna baru..."
              @focus="focusInput"
              @blur="blurInput"
            />
          </div>
          <div class="q-gutter-md q-ml-none q-mr-sm">
            <q-icon name="shopping_basket" color="white" class="profile-icon" style="font-size: 34px;" />
            <q-icon name="account_circle" color="white" class="profile-icon" style="font-size: 34px;" />
            <q-btn icon="notifications" class="q-ml-md">
              <q-badge floating color="red" rounded />
            </q-btn>
          </div>
        </div>
        <div class="tab-container">
          <q-tabs align="left" class="tab-align">
            <q-route-tab to="/page1" label="HOME" icon="home" />
            <q-route-tab to="/page2" label="PRODUCT" icon="store" />
          </q-tabs>
        </div>
      </q-header>

      <q-page-container class="q-pa-md" @scroll="handleScroll">
        <router-view />
        <div class="q-pa-md">
          <q-carousel
            animated
            v-model="slide"
            arrows
            navigation-label="..."
            infinite
            :autoplay="autoplay"
            prev-icon="<" 
            next-icon=">" 
            height="300px"
            width="100%"
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
    let autoplay = true;

    const handleScroll = () => {};

    const clearSearch = () => {
      text.value = '';
    };

    const focusInput = () => {
      text.value = '';
    };

    const blurInput = () => {
      if (!text.value) {
        text.value = '';
      }
    };

    return {
      slide,
      text,
      handleScroll,
      clearSearch,
      autoplay,
      focusInput,
      blurInput
    };
  },
};
</script>

<style scoped>
.toolbar {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.tab-container {
  display: flex;
  justify-content: center;
  margin-left: 10px;
}

.tab-align {
  max-width: 100%;
  overflow-x: auto;
}

.search-input {
  display: flex;
  align-items: center;
  margin-right: -100px;
  position: relative;
}

.search-label {
  display: flex;
  align-items: center;
  font-size: 14px;
  font-weight: bold;
  letter-spacing: 0.5px;
  cursor: text;
  color: white;
}

.search-textbox {
  width: 700px;
  font-size: 14px;
  padding: 8px;
  border-radius: 5px;
  margin-right: 300px;
  border: 1px solid #ccc;
  box-shadow: 0 0 5px rgba(0, 0, 0, 0.1);
}

.search-icon {
  cursor: pointer;
}

.q-carousel-slide img {
  height: 200px;
  object-fit: cover;
}

.footer {
  padding: 10px;
  margin-top: 10px;
  margin-bottom: 20px;
}

.footer-text,
.footer2 {
  font-size: 12px;
}
</style>
