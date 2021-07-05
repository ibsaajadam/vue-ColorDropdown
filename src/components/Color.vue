<template>
  <div :style="`backgroundColor:${backgroundColor}`" class="color">
    <div class="form">
    <h2 class="header">Enter a Color Below:</h2>
    <div class="input">
      <input type="text" v-model="color">
      <button class="button" @click="search">Search</button>
    </div>
      <Modal :show="showModal">
        <div v-if="currentColor">
          <div :style="`color:${currentColor.hex}`">{{ currentColor.label }}</div>
        </div>
        <div v-else class="not-found">
          <p>Color not found</p>
        </div>
        <button class="close" @click="close">Close</button>
      </Modal>
    </div>
    <div class="hints">
      <h4 class="color-title" @click="toggleColors">Example Colors<span class="click"><br>(click me)</span></h4>
      <div v-if="showColors">
        <ul class="colors">
          <li>Red</li>
          <li>Blue</li>
          <li>Yellow</li>
          <li>Green</li>
          <li>Orange</li>
        </ul>
      </div>
    </div>

  </div>
</template>

<script>
import Modal from './Modal.vue'
import { colors } from '../data.js'

  export default {
    components: { Modal },
    data() {
      return {
        color: '',
        colors: colors,
        showModal: false,
        showColors: false
      }
    },
    methods: {
      search() {
        this.showModal = true
      },
      close() {
        this.showModal = false
      },
      toggleColors() {
        this.showColors = !this.showColors
      }
    },
    computed: {
      currentColor(){
        if(this.color.toLowerCase() in colors) {
          return colors[this.color.toLowerCase()]
        }
        return null
      },
      backgroundColor(){
        if(this.currentColor){
          return this.currentColor.hex
        }
        return '#fff'
      }
    }
    
  }
</script>

<style lang="scss" scoped>
@import '../scss/variables.scss';
@import '../scss/color.scss';
</style>