<template>
  <div class="container">
    <h1 class="title">Ini adalah website vue sederhana saya</h1>
    <div class="input-container">
      <h2 :class="{ 'red-text': isRed }">Hello, {{ name }}!</h2>
      <input type="text" v-model="name" @input="changeTextColor" class="input-field">
    </div>
    <div class="text-description">
      <p :style="{ color: textColor, fontSize: '20px' }">
        Berikan inputan beberapa karakter, maka tulisan ini dapat berubah warna, dan tombol dibawah juga dapat mengubah warna.
      </p>
    </div>
    <div class="button-container">
      <button @click="changeText" :disabled="name.length < 5" class="color-button">Ubah Warna Teks</button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      name: '',
      isRed: false,
      textColor: 'black',
    };
  },
  methods: {
    changeTextColor() {
      this.isRed = this.name.length > 5;
      this.textColor = this.isRed ? 'red' : 'black';
    },
    changeText() {
      this.isRed = !this.isRed;
      this.textColor = this.isRed ? 'blue' : 'black';
    }
  }
};
</script>

<style scoped>
.container {
  max-width: 600px;
  margin: 0 auto;
  padding: 20px;
  background-color: #5a003f;
  border-radius: 10px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

.title {
  font-size: 32px;
  margin-bottom: 20px;
}

.input-container {
  margin-bottom: 20px;
}

.input-field {
  font-size: 20px;
  padding: 5px;
  width: 100%;
  border-radius: 5px;
}

.text-description {
  text-align: left;
  margin-bottom: 20px;
}

.color-button {
  font-size: 20px;
  padding: 10px 20px;
  border: none;
  border-radius: 5px;
  background-color: #4CAF50;
  color: white;
  cursor: pointer;
}

.color-button:disabled {
  background-color: #cccccc;
  cursor: not-allowed;
}

.red-text {
  color: red;
}
</style>
