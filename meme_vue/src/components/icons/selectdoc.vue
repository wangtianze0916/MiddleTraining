<script setup>
import { ref } from "vue";

const docSrc = ref();

function uploadDocument(e) {
  // Upload document and preview
  let file = e.target.files[0]; // Get the first file
  let doc = new FileReader();
  doc.readAsDataURL(file);

  doc.onload = ({ target }) => {
    docSrc.value = target.result; // Convert the document to binary data
  };
}
</script>

<template>
  <div>
    <input class="input_document left" type="file" @change="uploadDocument($event)" accept=".pdf, .doc, .docx" />
    <img class="show_input_document left" :src="docSrc" alt="Document Preview" />
  </div>
</template>

<style scoped>
.show_input_document {
  position: absolute;
  left: 10px;
  width: 130px;
  height: 130px;
}

.input_document {
  position: relative;
  width: 130px;
  height: 130px;
  background-color: blue;
  z-index: 999;
  opacity: 0;
}
</style>
