<script setup>
import { ref } from "vue";

const props = defineProps({
  title: String,
  content: String,
  id: Number,
});

function deleteNote() {
  fetch("http://localhost:3000/notes/" + props.id, {
    method: "DELETE",
  });
}
</script>

<template class="note">
  <h2>{{ props.title }}</h2>
  <p>{{ props.content }}</p>
  <button @click="">Edit</button>
  <button type="submit" @click="deleteNote()">Delete</button>
</template>
