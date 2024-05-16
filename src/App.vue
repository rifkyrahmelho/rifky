<template>
  <div id="app">
    <NoteList :notes="notes" :addNote="addNote" :removeNote="removeNote" />
  </div>
</template>

<script setup>
import { ref } from "vue";
import NoteList from "./components/NoteList.vue";

const notes = ref([]);
const newNote = ref("");

const addNote = () => {
  if (newNote.value.trim() !== "") {
    notes.value.push({
      id: notes.value.length + 1,
      content: newNote.value.trim(),
    });
    newNote.value = "";
  }
};

const removeNote = (noteToRemove) => {
  notes.value = notes.value.filter((note) => note.id !== noteToRemove.id);
};
</script>

<style>
* {
  justify-content: center;
}
#app {
  display: flex;
  align-items: center;
  text-align: center;
  font-family: Arial, sans-serif;
  margin: 20px;
  justify-content: center;
  position: relative;
}
input {
  width: 300px;
  padding: 10px;
  margin-bottom: 10px;
}
button {
  padding: 10px 20px;
  margin-left: 10px;
  cursor: pointer;
}
</style>
