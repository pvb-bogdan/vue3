<template>
  <h1>{{title}}</h1>
  <teleport to=".modals" v-if="showModal">
    <ModalSlots
      :theme="theme"
      @closeModal="toggleModal">
      <!-- slot whit a name-->
      <template v-slot:links>
        <a href="#">Link no.1</a>
        <a href="#">Link no.2</a>
      </template>
      <!-- default content for slot-->
      <h2>TESTAREA Modal 1</h2>
      <p>Lorem ipsum dolor sit amet consectetur, adipisicing elit. Explicabo, voluptatem!</p>
    </ModalSlots>
  </teleport>

  <div v-if="showModal2">
    <ModalSlots
      @closeModal="toggleModal2">
      <!-- default content for slot-->
      <h2>TESTAREA Modal 2</h2>
      <p>Lorem ipsum dolor sit amet consectetur, adipisicing elit. Explicabo, voluptatem!</p>
    </ModalSlots>
  </div>
  <div>
    <test/>
  </div>
  <button @click.shift="toggleModal">Open Modal (click+shift)</button>
  <button @click="toggleModal2">Open Modal 2</button>
</template>

<script>

import ModalSlots from './components/ModalSlots'
import test from './components/test_component'

export default {
  name: 'App',
  components: { ModalSlots, test },
  data (){
    return{
      title:'Teleport Project :)',
      theme: 'sale',
      text: 'More text send from parent form props',
      showModal: false,
      showModal2: false
    }
  },
  methods: {
    toggleModal (){
      this.showModal = !this.showModal
    },
    toggleModal2 (){
      this.showModal2 = !this.showModal2
    }
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;

  h1{
    color:red;
  }
}
</style>
