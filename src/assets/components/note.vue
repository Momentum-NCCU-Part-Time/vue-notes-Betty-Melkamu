<script setup>
const props = defineProps({
  title: String,
  content: String,
});

function deleteNote() {
fetch("http://localhost:3000/notes/", {
  method: "DELETE",
})
  .then((res) => res.json())
  .then((data) => (notesList.value = data));
}
</script>

<template class="note">
  <h2>{{ props.title }}</h2>
  <p>{{ props.content }}</p>
  <button @click = >Edit</button>
  <button @click = "" >Delete</button>
</template>
