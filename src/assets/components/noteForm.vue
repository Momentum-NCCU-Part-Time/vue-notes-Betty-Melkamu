<script setup>
import { ref } from "vue";

const noteTitle = ref("");
const noteBody = ref("");

function createNote() {
  fetch("http://localhost:3000/notes/", {
    method: "POST",
    headers: { "Content-Type": "application/json" },
    body: JSON.stringify({ title: noteTitle.value, body: noteBody.value }),
  })
    .then((res) => res.json())
    .then((data) => (notesList.value = data));
}
</script>

<template>
  <form id="noteCreation" @submit.prevent="createNote">
    <h2>{{ noteTitle }}</h2>
    <label name="title" id="title">Note Title</label>
    <input type="text" v-model="noteTitle" />
    <label name="body" id="body">{{ noteBody }}</label>
    <textarea type="text" v-model="noteBody" />
    <button for="btn" action="submit">Post</button>
  </form>
</template>
