<template>
  <div id="app">
    <Notebook @change-note="changeNote" @new-note="newNote" :notes="notes" :activeNote="index" />
    <Note @save-note="saveNote" @delete-note="deleteNote" :note="notes[index]" />
  </div>
</template>

<script>
import Notebook from './components/Notebook'
import Note from './components/Note'

export default {
  name: 'App',
  components: {
    Notebook,
    Note
  },
  data: () => ({
    notes: [],
    index: 0
  }),
  methods: {
    newNote() {
      this.notes.push({
        title: '',
        content: ''
      })
      this.index = this.notes.length -1
    },
    changeNote (index) {
      this.index = index
    },
    saveNote() {

    },
    deleteNote() {
      this.notes.splice(this.index, 1)
      this.index = Math.max(this.index - 1, 0)
    }
  }
}
</script>

<style>
  html, body, #app {
      height: 100%;
}
  body {
      margin: 0;
  }
  #app {
      font-family: 'Avenir', Helvetica, Arial, sans-serif;
      display: flex;
      flex-direction: row;
  }

</style>
