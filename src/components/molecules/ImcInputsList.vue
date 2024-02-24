<template>
  <div class="imc-input-list">
    <ImcInput
      label="Enter your height in centimeters"
      input-id="imc-height"
      v-model:value="height"
      v-model:error="heightError"
    />
    <ImcInput
      label="Enter your weight in kilograms"
      input-id="imc-weight"
      v-model:value="weight"
      v-model:error="weightError"
    />
  </div>
</template>

<script setup>
import ImcInput from '../atoms/ImcInput.vue'
const height = defineModel('height')
const weight = defineModel('weight')
const heightError = defineModel('heightError')
const weightError = defineModel('weightError')
</script>

<style scoped>
.imc-input-list {
  display: flex;
  flex-direction: column;
  gap: 20px;
}

@media screen and (min-width: 768px) {
  .imc-input-list {
    flex-direction: row;
  }
}
</style>
