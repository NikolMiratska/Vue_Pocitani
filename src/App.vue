<template>
  <div class="container">
    <h1>Převod váhy na počet <br> kusů třešní</h1>
    <div class="input-container">
      <label for="weight">Váha (kg): </label>
      <input v-model.number="weight" type="number" id="weight" />
    </div>
    <div class="result-container">
      <p>{{ weight }} kg je přibližně {{ convertWeightToCherries() }} kusů třešní.</p>
    </div>
  </div>

  <div class="container-count">
    <h1>Přidání a odebrání položek</h1>
    <div class="count">
      Počet: {{ count }}
      <span v-if="maxCount !== null">/ {{ maxCount }}</span>
    </div>
    <div>
      <button @click="decrement" :disabled="count === 0">Odebrat</button>
      <button @click="increment" :disabled="count === maxCount"> Přidat</button>
      <button @click="reset">Reset</button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      weight: 0,
      cherryWeight: 0.01, // Jedna tresen vazi 10 gramu (0.01 kg)

      count: 0,
      maxCount: 10
    };
  },

  methods: {
    convertWeightToCherries() {
      return Math.floor(this.weight / this.cherryWeight);
    },

    increment() {
      if (this.count < this.maxCount || this.maxCount === null) {
        this.count++;
      }
    },
    decrement() {
      if (this.count > 0) {
        this.count--;
      }
    },
    reset() {
      this.count = 0;
    }
  }
};



</script>


<style scoped>
.container {
  text-align: center;
  margin: 40px;
  border: 2px #333 solid;
  padding: 30px;
}
.input-container {
  padding: 12px 20px;
  margin: 8px 0;
}
.result-container {
  font-size: 20px;
}

.container-count {
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
  margin: 40px;
  border: 2px #333 solid;
  padding: 30px;
}
.count {
  font-size: 24px;
  margin-bottom: 20px;
}
button {
  background-color: #4CAF50;
  color: white;
  padding: 14px 20px;
  margin: 8px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  display:inline-block;
}
button:hover {
  background-color: #45a049;
}
button:disabled {
  background-color: #204b22;
  color: #a1a0a0;
}

</style>
