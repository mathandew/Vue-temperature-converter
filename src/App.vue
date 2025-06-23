<template>
  <div class="app">
    <h1>🌡️ Universal Temperature Converter</h1>

    <div class="converter-box">
      <!-- Unit selector -->
      <label for="unit">Select Input Unit:</label>
      <select id="unit" v-model="selectedUnit">
        <option value="celsius">Celsius (°C)</option>
        <option value="fahrenheit">Fahrenheit (°F)</option>
        <option value="kelvin">Kelvin (K)</option>
      </select>

      <!-- Temperature input -->
      <label for="input">Enter Temperature:</label>
      <input
        id="input"
        type="number"
        v-model.number="inputValue"
        placeholder="Enter temperature"
      />

      <!-- Output Results -->
      <div class="results">
        <p v-if="selectedUnit !== 'celsius'">🌡️ Celsius: <strong>{{ toCelsius }} °C</strong></p>
        <p v-if="selectedUnit !== 'fahrenheit'">🔥 Fahrenheit: <strong>{{ toFahrenheit }} °F</strong></p>
        <p v-if="selectedUnit !== 'kelvin'">❄️ Kelvin: <strong>{{ toKelvin }} K</strong></p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      inputValue: 0,
      selectedUnit: "celsius",
    };
  },
  computed: {
    // Convert to Celsius
    toCelsius() {
      switch (this.selectedUnit) {
        case "fahrenheit":
          return ((this.inputValue - 32) * 5 / 9).toFixed(2);
        case "kelvin":
          return (this.inputValue - 273.15).toFixed(2);
        default:
          return this.inputValue.toFixed(2);
      }
    },

    // Convert to Fahrenheit
    toFahrenheit() {
      switch (this.selectedUnit) {
        case "celsius":
          return ((this.inputValue * 9 / 5) + 32).toFixed(2);
        case "kelvin":
          return (((this.inputValue - 273.15) * 9 / 5) + 32).toFixed(2);
        default:
          return this.inputValue.toFixed(2);
      }
    },

    // Convert to Kelvin
    toKelvin() {
      switch (this.selectedUnit) {
        case "celsius":
          return (this.inputValue + 273.15).toFixed(2);
        case "fahrenheit":
          return (((this.inputValue - 32) * 5 / 9) + 273.15).toFixed(2);
        default:
          return this.inputValue.toFixed(2);
      }
    }
  }
};
</script>

<style scoped>
.app {
  text-align: center;
  margin-top: 40px;
  font-family: Arial, sans-serif;
}

.converter-box {
  background-color: #f9f9f9;
  padding: 30px;
  width: 350px;
  margin: auto;
  border-radius: 10px;
  box-shadow: 0 0 12px rgba(0, 0, 0, 0.15);
}

label {
  display: block;
  margin-top: 15px;
  font-weight: bold;
}

select,
input {
  width: 90%;
  padding: 10px;
  margin-top: 8px;
  font-size: 16px;
  border-radius: 6px;
  border: 1px solid #ccc;
}

.results {
  margin-top: 25px;
}

.results p {
  font-size: 18px;
  font-weight: bold;
}
</style>
