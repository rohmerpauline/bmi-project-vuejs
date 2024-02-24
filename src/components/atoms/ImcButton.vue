<script setup>
const height = defineModel('height')
const weight = defineModel('weight')
const bmi = defineModel('bmi')
const heightError = defineModel('heightError')
const weightError = defineModel('weightError')
const errorMessage = defineModel('errorMessage')

const calculateBMI = () => {
  if (typeof weight.value !== 'number' || weight.value === 0) {
    weightError.value = true
  } else {
    weightError.value = false
  }
  if (typeof height.value !== 'number' || height.value === 0) {
    heightError.value = true
  } else {
    heightError.value = false
  }

  if (typeof weight.value !== 'number' || typeof height.value !== 'number') {
    errorMessage.value = 'Both your height and weight should be numbers.'
  } else if (weight.value === 0 || height.value === 0) {
    errorMessage.value = 'Enter a weight and height superior to 0.'
  } else if (typeof weight.value === 'number' && typeof height.value === 'number') {
    errorMessage.value = null
  }
  if (
    typeof weight.value !== 'number' ||
    typeof height.value !== 'number' ||
    height.value === 0 ||
    weight.value === 0
  ) {
    bmi.value = undefined
  } else {
    const heightInMeters = height.value / 100
    const calculatedBmi = weight.value / Math.pow(heightInMeters, 2)
    bmi.value = Math.round(calculatedBmi * 10) / 10
  }

  console.log(bmi.value)
}
</script>

<template>
  <div class="imc-button">
    <button type="button" @click="calculateBMI">Calculate your BMI</button>
  </div>
</template>

<style scoped>
.imc-button {
  text-align: center;
  margin-top: 20px;
}

.imc-button button {
  height: 35px;
  background-color: rgb(237, 182, 63);
  border-radius: 8px;
  padding: 10px 15px;
  font-weight: 700;
  font-size: 13px;
}
</style>
