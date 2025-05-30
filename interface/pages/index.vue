<template>
  <div class="flex">
    <div class="flex items-center gap-8 w-full">
      <!-- Tomato image -->
      <UiInformasion />
      <!-- Input File -->
      <UiInputFile />
    </div>
  </div>
</template>

<script setup>
import { UiInputFile, UiInformasion } from "#components";
import { ref } from "vue";

const imagePreview = ref(null);

const onFileChange = (e) => {
  const file = e.target.files[0];
  if (file && file.type.startsWith("image/")) {
    const reader = new FileReader();
    reader.onload = () => {
      imagePreview.value = reader.result;
    };
    reader.readAsDataURL(file);
  }
};

const removeImage = () => {
  imagePreview.value = null;
  document.getElementById("restaurantImage").value = null;
};
</script>
