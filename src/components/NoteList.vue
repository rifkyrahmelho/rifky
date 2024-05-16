<template>
  <main class="app">
    <section class="create-note">
      <h3><b>Create New Note</b></h3>
      <form id="new-note-form" @submit.prevent="addNote">
        <input
          type="text"
          name="value"
          id="content"
          placeholder="Enter your note here..."
          v-model="newNote"
        />
        <button class="add-note">Add Note</button>
      </form>
    </section>

    <section class="note-list">
      <h3><b>Notes :</b></h3>
      <div v-for="note in notes" :key="note.id" class="note-content">
        <Note :note="note" @remove="removeNote" />
      </div>
    </section>
  </main>
</template>

<script setup>
import { ref } from "vue";
import Note from "./NoteItem.vue"; // Ensure the import path is correct

let id = 0;

const newNote = ref("");
const notes = ref([]);

function addNote() {
  if (newNote.value.trim() !== "") {
    notes.value.push({
      id: id++,
      content: newNote.value, // Ensure the property name is 'content'
    });
    newNote.value = "";
  }
}

function removeNote(note) {
  notes.value = notes.value.filter((n) => n !== note);
}
</script>

<style>
h3 {
  position: relative;
}
</style>
