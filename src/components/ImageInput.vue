<template>
  <Dropzone :url="url" @file-added="handleFile" />
</template>

<script>
import Dropzone from './Dropzone'
export default {
  name: 'ImageInput',
  components: {
    Dropzone
  },
  props: {
    url: String
  },
  methods: {
    handleFile (file) {
      console.log(file)
    }
  }
}
</script>