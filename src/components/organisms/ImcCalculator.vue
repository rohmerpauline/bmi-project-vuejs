<script setup>
import ImcBox from '../templates/ImcBox.vue'
import ImcInputsList from '../molecules/ImcInputsList.vue'
import ImcButton from '../atoms/ImcButton.vue'
import ImcResult from '../molecules/ImcResult.vue'
import { ref } from 'vue'

const height = ref()
const weight = ref()
const bmi = ref()
const heightError = ref(false)
const weightError = ref(false)
const errorMessage = ref(null)
</script>

<template>
  <ImcBox>
    <h1><span>BMI</span> Calculator</h1>
    <form>
      <ImcInputsList
        v-model:weight="weight"
        v-model:height="height"
        v-model:weightError="weightError"
        v-model:heightError="heightError"
      />
      <ImcButton
        v-model:weight="weight"
        v-model:height="height"
        v-model:bmi="bmi"
        v-model:heightError="heightError"
        v-model:weightError="weightError"
        v-model:errorMessage="errorMessage"
      />
    </form>
    <ImcResult v-if="bmi !== undefined" v-model="bmi" />
    <p v-if="errorMessage" class="error-message">{{ errorMessage }}</p>
  </ImcBox>
</template>

<style scoped>
h1 {
  text-align: center;
  font-size: 23px;
  margin-bottom: 15px;
}

h1 span {
  font-weight: 600;
}

.error-message {
  text-align: center;
  margin-top: 15px;
  color: red;
  font-size: 12px;
  font-weight: 700;
}
</style>
