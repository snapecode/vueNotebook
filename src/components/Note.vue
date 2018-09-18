
//First we check if we have valid note data to work with and if not, it will display a message
//telling the user how to start using the app. Once we have a note, we bind two modals, one
//being note.title and the other being  note.content. Finally, we have our two buttons to handle
//our two supported operations for this component, deleting the current note, and saving the
//current note.

<template></template>
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
