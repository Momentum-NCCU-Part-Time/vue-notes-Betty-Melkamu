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

function editNote() {
  fetch("http://localhost:3000/notes/" + props.id, {
    method: "PATCH",
    headers: { "Content-Type": "application/json" },
    body: JSON.stringify({ title: noteTitle.value, body: noteBody.value }),
  })
    .then((res) => res.json())
    .then((data) => (notesList.value = data));
}
</script>

<template class="note">
  <h2>{{ props.title }}</h2>
  <p>{{ props.content }}</p>
  <button @click="editNote()">Edit</button>
  <button @click="deleteNote()">Delete</button>
</template>
