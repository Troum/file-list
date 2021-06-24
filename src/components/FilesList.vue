<template>
  <ul>
    <template v-for="(file, i) in files">
      <li :key="i" v-show="isActive(file)">
        {{ file }}
      </li>
    </template>
  </ul>
</template>

<script>
export default {
  name: 'FileList',
  props: {
    filesPriority: null,
    filesActive: null
  },
  mounted() {
    console.log(this.files)
  },
  methods: {
    isActive (file) {
      return this.actives.includes(file)
    }
  },
  computed: {
    actives () {
      return this.filesActive
    },
    files () {
      const files = this.$store.state.files
      const sorted = Object.fromEntries(
          Object.entries(this.filesPriority).sort(([, a], [, b]) => b - a)
      )
      return Object.keys(sorted).filter((item) => {
        return files.filter((file) => {
          return item === file
        })
      })
    }
  }
}
</script>
