# NotePad

> A Vue.js project for a notepad that acts similar to Apple Notes.
> 
> Note that this version is using Firebase to record the addition, update, and deletion of notes.
>
 >You will have to setup your own firebase database and replace my api keys with your own:



## Build Setup

``` bash
# install dependencies

1.npm install
2.Change settings in App.vue to your firebase: 
-
var database = Firebase.initializeApp({
      apiKey: 'apiKey',
      authDomain: 'authDomain',
      databaseURL: 'databaseURL',
      projectId: 'projectId',
      storageBucket: 'storageBucket',
      messagingSenderId: 'messagingSenderId'
  }).database().ref();
 - 
3.npm install firebase --save 

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build

# build for production and view the bundle analyzer report
npm run build --report
```

For a detailed explanation on how things work, check out the [guide](http://vuejs-templates.github.io/webpack/) and [docs for vue-loader](http://vuejs.github.io/vue-loader).
