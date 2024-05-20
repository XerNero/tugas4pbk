<template>
  <div>
    <!-- Tombol yang memicu pengiriman data ke App.vue -->
    <button @click="sendData">Show Game Info</button>
  </div>
</template>

<script>
  export default {
    name: 'Emit', // Nama komponen yang akan di deklarasikan di App.vue

    emits: ['dataSent'], // Deklarasi event 'dataSent' yang akan di-emite ke App.vue
    methods: {
      sendData() {
        // Emit event 'dataSent' dengan data yang dikirimkan ke App.vue
        this.$emit('dataSent'); // Mengirimkan event tanpa data tambahan
      }
    }
  }
</script>
