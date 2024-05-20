<template>
  <div class="app">
    <h1>Game Information App</h1>
    <Emit @dataSent="handleData" /> <!-- Memanggil komponen Emit dan menangani event 'dataSent' -->
    <p v-if="receivedData" class="receive"> {{ receivedData.name }}</p> <!-- Menampilkan nama game yang diterima --> <!--TAMBAHKAN CLASS pas edit h-2-->
    <Slot v-if="receivedData"> <!-- Memanggil komponen Slot dan meneruskan konten ke dalam slot -->
      <!-- Menampilkan informasi game yang diteruskan dari Emit.vue -->
      <p>
        {{ receivedData.name }} is an {{ receivedData.genre }} game developed and published by {{ receivedData.publisher }}.
      </p>
    </Slot>
  </div>
</template>

<script>
import Emit from './components/Emit.vue'; // Mengimpor komponen Emit
import Slot from './components/Slot.vue'; // Mengimpor komponen Slot

export default {
  name: 'App',
  components: {
    Emit, // Mendeklarasikan komponen Emit
    Slot  // Mendeklarasikan komponen Slot
  },
  data() {  // Berhubungan langsung dengan Slot.vue untuk menampilkan informasi dari game yang di pilih ya intinya itu lah dah pusing
    return {
      games: [
        { name: 'Apex Legends', genre: 'free-to-play battle royale shooter game where legendary characters with powerful abilities team up to fight for fame and fortune on the outskirts of the Frontier.', publisher: 'Electronic Arts' },
        { name: 'Fornite', genre: 'a survival game where 100 players battle each other in a player versus player battle to be the last one standing, and in Fortnite there are many different types of game modes that can be played', publisher: 'Epic Games' },
        { name: 'Valorant', genre: 'fps game and 4 teammates face off against 5 other Agents in a shootout with one life per round to be the first to win 13 rounds!', publisher: 'Riot Games' },
        { name: 'Roblox', genre: 'online gaming platforms and game creation systems that allow users to program games and play games created by other users', publisher: 'Roblox Corporation Arts' },
        { name: 'Minecraft', genre: 'sandbox video game. Minecraft allows players to explore, build, and survive in an open world made of 3D blocks.', publisher: 'Mojang' }
        // Tambahkan game lainnya di sini
      ],
      currentIndex: 0, // Menunjukkan indeks game yang sedang ditampilkan
      receivedData: null
    };
  },
  methods: {
    handleData() {
      this.receivedData = this.games[this.currentIndex]; // Menyimpan data game yang diterima
      this.currentIndex = (this.currentIndex + 1) % this.games.length; // Pindah ke game berikutnya (dengan melingkar)
    }
  }
}
</script>

<style>
  .app {
  max-width: 600px;
  margin: auto;
  border: 5px solid gray;
  border-radius: 20px;
  padding: 20px;
  background-image: url('https://r4.wallpaperflare.com/wallpaper/684/971/825/studio-ghibli-anime-cartoon-japanese-my-neighbor-totoro-hd-wallpaper-9886add810b0bcd8a06ce13e78a2547a.jpg');
  background-size: cover;
  background-position: center;
  background-color: rgba(255, 255, 255, 10); 
  text-align: center;
  color: white;
  }
  
  .receive {
    background-color: #f9f9f9;
    border: 1px solid #ddd;
    padding: 20px;
    margin-top: 20px;
    border-radius: 8px;
    color: black;
  }
</style>