<template>
  <h1> {{pageTitle}}</h1>
  <h3>Welcome....</h3>
  <div v-if="showModal">
      <!-- <Modal 
        :modalTitle="modalTitle" 
        :modalText="modalText" 
        theme="sale" 
        @close-modal="toggleModal" /> -->

        <Modal theme="sale" @close-modal="toggleModal" >
          <h1>Cash Giveaway</h1>
          <p>Win cash and prizes</p>
          <template v-slot:links>
            <a href="#">Sign Up</a>
            <a href="#">Sign In</a>
          </template>
        </Modal>
  </div>

  <teleport to='.modals'  v-if="showModalTwo">
    <Modal @close-modal="toggleModalTwo">
        <h1>Modal 2</h1>
        <p>small content for modal 2</p>
       
    </Modal>
  </teleport>

  <button @click="toggleModal">Open Modal</button>
  <button @click="toggleModalTwo">Open Modal2</button>
</template>

<script>

import Modal from './components/Modal'

export default {
  name: 'App',
  components: {
    Modal
  },
  data(){
    return {
      pageTitle: 'Modal Pop Up Project',
      modalTitle: 'Sign up for the giveaway',
      modalText: 'Grab Your ninja swag fro half the price',
      showModal: false,
      showModalTwo: false
    }
  },
  methods: {
      toggleModal(){
        this.showModal = !this.showModal;
      },
      toggleModalTwo(){
        this.showModalTwo = !this.showModalTwo
    },
}
}
</script>

<style>
#app, .modals {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
button{
  margin: 10px;
}
</style>
