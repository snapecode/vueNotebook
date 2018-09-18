
<template>
      <div class="note">
        <div v-if="note">
          <label for="title">Title</label>
          <input type="text" v-model="note.title" class="title" name="title" placeholder="Enter a title" />
          <label for="content">Content</label>
          <textarea class="content" name="content" v-model="note.content" placeholder="Enter some Content"></textarea>
          <button @click="deleteNote()">Delete Note</button>
          <button @click="saveNote()">Save Note</button>
        </div>
        <div v-else>
          <h1>&larr; To Start, create a new note!</h1>
        </div>
      </div>
</template>

<script>
  export default {
    name: 'Note',
    props: ['note'],
    methods: {
      deleteNote() {
        this.$emit('delete-note')
      },
      saveNote() {
        this.$emit('save-note')
      }
    }
  }
</script>

<style scoped>
  .note {
    width: 100%;
    padding: 2rem;
    box-shadow: 3rem 0 5rem 3rem #1e90ff;
  }

  .content, .title {
    border-style: none;
    border-radius: 0.25rem;
    border: solid 1px darkgrey;
    width: 100%;
    box-sizing: border-box;
    margin-bottom: 1.25rem;
  }

  .content:focus, .title:focus {
    outline: 0;
  }

  .content {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    resize: vertical;
    font-size: 1.5rem;
    padding: 0.5rem;
    height: 20rem;
  }

  .title {
    font-size: 2rem;
    padding: 0.5rem 1rem;
  }

  label {
    margin-bottom: 0.5rem;
    display: inline-block;
  }

  button {
    border-style: none;
    padding: 0.5rem 0.75rem;
    background-color: #44ab22;
    margin-right: 1rem;
    border-radius: 0.25rem;
    color: #808080;
    font-size: 1rem;
    cursor: pointer;
  }

  button:hover {
    background-color: #00bfff;
  }
</style>


