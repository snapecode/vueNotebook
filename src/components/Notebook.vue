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
  .notebook {
    max-width: 20rem;
    width: 30rem;
    background: #ecfcff;
  }

  ul {
    list-style-type: none;
    padding: 0;
    margin: 0;
    height: 100%;
    position: relative;
  }

  li {
    padding: 1rem;
    font-size: 1.25rem;
    min-height: 1.5rem;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
  }

  li:hover {
    cursor: pointer;
    background-color: #a9a9a9;
  }

  .active {
    background-color: #1e90ff;
  }

  .active:hover {
    background-color: #1e90fd;
  }

  .new-note {
    background-color: #4169e1;
    color: #808080;
    position: absolute;
    bottom: 0;
    width: 100%;
    box-sizing: border-box;
  }

  .new-note:hover {
    background-color: #000080;
  }
</style>
