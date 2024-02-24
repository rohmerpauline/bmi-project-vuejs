<script setup>
import { computed } from 'vue'
const bmi = defineModel()

const computedResults = computed(() => {
  const bmiValue = bmi.value
  let bmiClass, bmiMessage

  if (bmiValue >= 19 && bmiValue <= 25) {
    bmiClass = 'green'
    bmiMessage = 'Your BMI is in the healthy range.'
  } else if ((bmiValue > 25 && bmiValue <= 30) || (bmiValue >= 16.5 && bmiValue <= 19)) {
    bmiClass = 'orange'
    bmiMessage = 'Your BMI indicates a warning.'
  } else if (bmiValue < 16.5 || bmiValue > 30) {
    bmiClass = 'red'
    bmiMessage = 'Your BMI is in the high-risk range.'
  } else {
    bmiClass = 'unknown'
    bmiMessage = null
  }

  return { bmiClass, bmiMessage }
})
</script>

<template>
  <div class="imc-result">
    <div class="bmi-result" :class="computedResults.bmiClass">{{ bmi }}</div>
    <p class="bmi-message" v-if="computedResults.bmiMessage">{{ computedResults.bmiMessage }}</p>
  </div>
</template>

<style scoped>
.imc-result {
  text-align: center;
  margin-top: 15px;
}

.bmi-result {
  font-size: 25px;
  font-weight: 700;
}

.bmi-message {
  font-weight: 300;
  font-size: 13px;
}

.green {
  color: green;
}

.orange {
  color: orange;
}

.red {
  color: red;
}
</style>
