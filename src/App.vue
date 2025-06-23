<template>
  <div class="app">
    <h1>🌡️ Temperature Converter</h1>

    <div class="converter-box">
      <label for="celsius">Enter Celsius:</label>
      <input
        id="celsius"
        type="number"
        v-model="celsius"
        placeholder="Enter Celsius temperature"
      />

      <p :class="tempClass">
        Fahrenheit: <strong>{{ fahrenheit }} °F</strong>
      </p>
    </div>

    <p class="note">Dynamic styling applied based on temperature</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      celsius: 0,
      fahrenheitWatched: 32,
    };
  },
  computed: {
    fahrenheit() {
      return (this.celsius * 9) / 5 + 32;
    },
    tempClass() {
      if (this.fahrenheit < 32) return 'cold';
      if (this.fahrenheit > 85) return 'hot';
      return 'normal';
    }
  },
  watch: {
    celsius(newVal) {
      this.fahrenheitWatched = (newVal * 9) / 5 + 32;
      console.log(`Watcher: Celsius changed to ${newVal}, Fahrenheit updated to ${this.fahrenheitWatched}`);
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
  background-color: #f5f5f5;
  padding: 20px;
  width: 300px;
  margin: auto;
  border-radius: 8px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

input {
  margin-top: 10px;
  padding: 10px;
  font-size: 16px;
  width: 80%;
  border: 1px solid #ccc;
  border-radius: 4px;
}

p {
  margin-top: 20px;
  font-size: 20px;
}

.note {
  margin-top: 30px;
  font-style: italic;
  color: #666;
}

.cold {
  color: #2196f3;
  font-weight: bold;
}

.normal {
  color: #4caf50;
  font-weight: bold;
}

.hot {
  color: #f44336;
  font-weight: bold;
}
</style>
