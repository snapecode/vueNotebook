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
    HelloWorld
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
