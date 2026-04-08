<template>
  <div class="container">
    <h1>Revert Text</h1>

    <textarea v-model="text" placeholder="Type something..."></textarea>

    <div class="buttons-container">
      <button @click="clearInput">Clear</button>
      <button class="submit" @click="handleSubmit">Submit</button>
    </div>

    <p v-if="showText">Texto enviado correctamente</p>
  </div>
</template>

<script setup>
import { ref } from "vue";

const text = ref("");
const showText = ref(false);

const clearInput = () => {
  text.value = "";
  showText.value = false;
};

const handleSubmit = () => {
  if (text.value.trim() !== "") {
    showText.value = true;
  }
};
</script>

<style>
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100vh;
  gap: 10px;
}

textarea {
  width: 450px;
  height: 100px;
}

.buttons-container {
  margin-top: 16px;
  display: flex;
  justify-content: space-between;
  gap: 16px;
}

button {
  padding: 5px 10px;
  padding: 12px 24px;
  border: none;
  border-radius: 16px;
}

.submit {
  background-color: #53A653;
}
</style>
