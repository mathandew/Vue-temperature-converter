<template>
  <div class="input-box">
    <label for="input">Enter Temperature:</label>
    <input
      id="input"
      type="number"
      :value="modelValue"
      @input="$emit('update:modelValue', parseFloat($event.target.value))"
      placeholder="Enter value"
    />
  </div>
</template>

<script>
export default {
  props: {
    modelValue: Number
  }
};
</script>

<style scoped>
.input-box {
  margin: 20px 0;
}
input {
  padding: 10px;
  width: 100%;
  font-size: 16px;
}
</style>
