<template>
  <div class="imc-input">
    <label :for="inputId">{{ label }}</label>
    <input
      :id="inputId"
      :type="inputType"
      class="input-field"
      :class="{ error: error }"
      required
      v-model="inputValue"
    />
  </div>
</template>

<script setup>
defineProps({
  label: String,
  inputId: String,
  inputType: {
    type: String,
    default: 'number'
  }
})

const inputValue = defineModel('value')
const error = defineModel('error')

/* const weight = ref(modelValue) */
</script>

<style scoped>
.imc-input {
  display: flex;
  flex-direction: column;
  width: 100%;
}

label {
  margin-bottom: 9px;
  font-size: 12px;
  font-weight: 500;
}

.input-field {
  border: 1px solid #ddd;
  height: 35px;
  border-radius: 5px;
  outline: none;
  padding: 5px 10px;
}

input:focus {
  border-color: #ddd;
  box-shadow: 0 0 5px rgba(115, 143, 173, 0.5);
}

.error {
  border-color: red;
}
</style>
