
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
