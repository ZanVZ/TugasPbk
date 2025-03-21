<template>
    <div>
      <h2>Daftar Barang</h2>
      <ul>
        <li v-for="(item, index) in items" :key="index">
          {{ index + 1 }}. {{ item.name }} - Rp{{ item.price }}
        </li>
      </ul>
      
      <h3>Total Harga: Rp{{ totalPrice }}</h3>
      
      <input ref="inputRef" type="text" v-model="newItem" placeholder="Tambah barang..." />
      <button @click="addItem">Tambah</button>
      
      <p>Jumlah barang: {{ itemCount }}</p>
    </div>
  </template>
  
  <script setup>
  import { ref, computed, watch, onMounted } from 'vue';
  
  const items = ref([
    { name: 'Laptop', price: 10000000 },
    { name: 'Mouse', price: 200000 },
    { name: 'Keyboard', price: 500000 }
  ]);
  
  const newItem = ref('');
  const inputRef = ref(null);
  
  const totalPrice = computed(() => items.value.reduce((sum, item) => sum + item.price, 0));
  const itemCount = computed(() => items.value.length);
  
  const addItem = () => {
    if (newItem.value.trim()) {
      items.value.push({ name: newItem.value, price: Math.floor(Math.random() * 1000000) });
      newItem.value = '';
    }
  };
  
  watch(items, (newVal) => {
    console.log('Daftar barang diperbarui:', newVal);
  }, { deep: true });
  
  onMounted(() => {
    inputRef.value.focus();
  });
  </script>