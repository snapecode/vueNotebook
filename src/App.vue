<template>
  <div id="app">
    <Notebook @change-note="changeNote" @new-note="newNote" :notes="notes" :activeNote="index" />
    <Note @save-note="saveNote" @delete-note="deleteNote" :note="notes[index]" />
  </div>
</template>

<script>
import Notebook from './components/Notebook'
import Note from './components/Note'
import Firebase from 'firebase'

var database = Firebase.initializeApp({
  apiKey: 'AIzaSyB8VrM8Y5Fj89sqXwXh4B0sjUoeBnVZSWQ',
  authDomain: 'notebook-c3090.firebaseapp.com',
  databaseURL: 'https://notebook-c3090.firebaseio.com',
  projectId: 'notebook-c3090',
  storageBucket: '',
  messagingSenderId: '28701007939'
}).database().ref();

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
  mounted() {
    database.once('value', (notes) =>{
      notes.forEach((note) => {
        this.notes.push({
          ref: note.ref,
          title: note.child('title').val(),
          content: note.child('content').val()
        })
      })
    })
  },
  methods: {
    newNote() {
      this.notes.push({
        title: '',
        content: ''
      });
      this.index = this.notes.length -1
    },
    changeNote (index) {
      this.index = index
    },
    saveNote() {
      var note = this.notes[this.index];
      if (note.ref){
        this.updateExistingNote(note)
      } else {
        this.insertNewNote(note)
      }
    },
    updateExistingNote(note){
      note.ref.set({
        title: note.tittle,
        content: note.content
      })
    },
    insertNewNote(note){
      note.ref = database.push(note)
    },
    deleteNote() {
      var ref = this.notes[this.index].ref;
      ref && ref.remove();
      this.notes.splice(this.index, 1);
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
