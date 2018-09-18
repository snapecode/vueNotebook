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
      this.index = MAth.max(this.index - 1, 0)
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
