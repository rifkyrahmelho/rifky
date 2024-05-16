<template>
  <div class="note-content">
    <p>{{ note.id + 1 }}. {{ note.content }}</p>
    <button @click="removeNote">Remove</button>
  </div>
</template>

<script setup>
import { defineProps, defineEmits } from "vue";

const props = defineProps({
  note: {
    type: Object,
    required: true,
  },
});

const emit = defineEmits(["remove"]);

function removeNote() {
  emit("remove", props.note);
}
</script>

<style>
/* Add your styling here */
</style>
