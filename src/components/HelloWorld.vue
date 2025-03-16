<template>
  <div>
    <p>Nama: {{ nama }}</p>
    <button @click="ubahNama">Ubah Nama</button>
    
    <p v-if="isOnline">User Sedang Online</p>
    <p v-else>User Sedang Offline</p>
    <button @click="toggleStatus">Ganti Status</button>
    
    <input v-model="nama" placeholder="Masukkan nama" />
    <p>Nama yang Anda ketik: {{ nama }}</p>
    
    <button @click="sayHello">Klik Aku</button>
    
    <p :style="{ color: warna }">Teks Berwarna</p>
    <button @click="gantiWarna">Ganti Warna</button>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const nama = ref('Budi');
const isOnline = ref(true);
const warna = ref('blue');

const ubahNama = () => {
  nama.value = 'Andi';
};

const toggleStatus = () => {
  isOnline.value = !isOnline.value;
};

const sayHello = () => {
  alert('Halo, selamat datang di Vue.js!');
};

const gantiWarna = () => {
  warna.value = warna.value === 'blue' ? 'red' : 'blue';
};
</script>
