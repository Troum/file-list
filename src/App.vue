<template>
  <div id="app">
    <files-list :files-priority="filesPriority" :files-active="filesActive"/>
  </div>
</template>

<script>
import FilesList from './components/FilesList.vue'

export default {
  name: 'App',
  components: {
    FilesList
  },
  data () {
    return {
      filesPriority: {
        fileA: 20,
        fileB: 10,
        fileC: 0,
      },
      filesActive: [
        'fileA',
        'fileB'
      ]
    }
  }
}
</script>
