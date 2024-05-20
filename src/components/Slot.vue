<template>
  <div class="slot-container">
    <h3>Game Information</h3>
    <!-- Slot untuk menampilkan konten yang diteruskan dari App.vue -->
    <slot></slot>
  </div>
</template>

<script>
export default {
  name: 'Slot' // Nama komponen yang akan di deklarasikan di App.vue
}
</script>

<style>
.slot-container {
  background-color: #f9f9f9; 
  border: 1px solid #ddd; 
  padding: 20px; 
  margin-top: 20px; 
  border-radius: 8px; 
  color: black; 
}
</style>
