<template>
<div class="notebook">
  <ul>
    <li
        v-for="(note, index) of notes"
        class="note"
        v-bind:class="{ 'active': index === activeNote}"
        @click="changeNote(index)"
        >
      <div> {{note.title}}</div>
    </li>
    <li class="new-note" @click="newNote()">New Note +</li>
  </ul>
</div>
</template>

<script>
    export default {
        name: "notebook",
      props: ['notes', 'activeNote' ],
      methods: {
          changeNote (index) {
            this.$emit('change-note', index)
          },
        newNote() {
            this.$emit('new-note')
        }
      }
    }
</script>

<style scoped>

</style>
