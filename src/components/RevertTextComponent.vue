<template>
  <div class="container">
    <h1>Revert Text</h1>

    <textarea v-model="textInput" placeholder="Type something..."></textarea>

    <div class="buttons-container">
      <button @click="clearInput">Clear</button>
      <button class="submit" @click="revertText">Submit</button>
    </div>

    <p v-if="revertedText.length > 0">{{ revertedText }}</p>
  </div>
</template>

<script setup>
import { ref } from "vue";

const textInput = ref("");
const revertedText = ref("");

const clearInput = () => {
  textInput.value = "";
  revertedText.value = "";
};

const revertText = () => {
  if (textInput.value.trim() !== "") {
    revertedText.value = textInput.value
      .split(" ")
      .map((word) => word.split("").reverse().join(""))
      .join(" ");
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
  background-color: #53a653;
}
</style>
