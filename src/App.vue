<script setup>
import { ref } from "vue";
import Note from "./assets/components/note.vue";
import noteForm from "./assets/components/noteForm.vue";
const notesList = ref([]);

fetch("http://localhost:3000/notes/", {
  method: "GET",
})
  .then((res) => res.json())
  .then((data) => (notesList.value = data));
</script>

<template>
  <div>
    <h1>Betty's Vue Notes App</h1>
    <ul>
      <li class="noteItem" v-for="noteItem in notesList">
        <Note
          v-model:title="noteItem.title"
          v-model:content="noteItem.body"
          v-model:id="noteItem.id"
        />
      </li>
    </ul>
    <button @click="createNote()" type="submit">Add Note</button>
  </div>
</template>

<style scoped></style>
