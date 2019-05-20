<template>
  <div id="app">
    <ImageInput url="https://www.tykue.ie">
      <input type="text" name="image_id">
    </ImageInput>
  </div>
</template>

<script>
import ImageInput from './components/ImageInput.vue'

export default {
  name: 'app',
  components: {
    ImageInput
  }
}
</script>

<style>
</style>
