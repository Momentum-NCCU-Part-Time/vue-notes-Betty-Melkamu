<script setup>
//We need to do this at the mount of the site, so we can make notes
import { ref } from "vue";
import Note from "./assets/components/note.vue";
const notesList = ref([]);
//Fetch from database
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
        <Note v-model:title="noteItem.title" v-model:content="noteItem.body" />

      </li>
    </ul>
    <button>Add Note</button>
  </div>
</template>

<style scoped></style>
