<template>
  <!-- <img alt="Vue logo" src="./assets/logo.png">
  <HelloWorld msg="Welcome to Your Vue.js App"/> -->
  
  <!-- <h1>My First Vue App</h1> -->
  <h1>{{title}}</h1>

  <p>Welcome...</p>

  <!-- <input type="text" ref="name">
  <button @click="handleClick">click me</button> -->

  <!-- <Modal header="Sign up for the Giveaway!" text="Grab your ninja swag for half price!"/> -->
  <!-- <Modal :header="header" :text="text" theme="sale"/> -->
  <teleport to=".models"  v-if="showModal"><!-- div yerine teleport to=".models" geldi -->
    <!-- <Modal :header="header" :text="text" theme="sale" @close="toggleModal"/>  Slot kullanıldığında header ve text'e gerek kalmadı-->
    <Modal theme="" @close="toggleModal">
      <template v-slot:links><!-- name of the slot is links - template dışındaki elemanlar default content -->
        <a href="#">sign up now</a>
        <a href="#">more info</a>
      </template>
      <h1>Ninja Giveaway!</h1>
      <p>Grab your ninja swag for half the price</p>
      <!-- <a href=""></a> -->
    </Modal>
  </teleport>
  <button @click.alt="toggleModal">Open Modal (alt)</button>

  <div v-if="showModal2">
    <Modal @close="toggleModal2">
      <template v-slot:exercise>
        <a href="#">Go somewhere</a>
        <a href="#"> Go somewhere else</a>
      </template>
      <h1>Hello!Sign up to the newsletter</h1>
      <p>this was my challenge in Vue JS 3 tutorial...</p>
    </Modal>
  </div>
  <button @click="toggleModal2">Open Modal2 </button>
  

  
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import Modal from './components/Modal.vue'

export default {
  name: 'App',
  // components: {
  //   HelloWorld
  // }
  components:{ Modal },

  data(){
    return{
      title: 'My First Vue App :)',
      header: 'Sign up for the Giveaway!',
      text: 'Grab your ninja swag for half price!',
      showModal: false,
      showModal2: false
    }
  },
  methods:{
    /* handleClick(){
      console.log(this.$refs.name)
      this.$refs.name.classList.add('active')
      this.$refs.name.focus()
    }, */
    toggleModal(){
      this.showModal = !this.showModal
    },

    toggleModal2(){
      this.showModal2 = !this.showModal2
    }

  }
}
</script>

// challenge                                                                         -DONE.
//   - create an extra button to open a different modal
//   - use the same modal component but pass in a different template (slot)
//   - use a different method (e.g. toggleModalTwo) and data ( e.g. showModalTwo)

<style>/* <style scoped> */
#app, .modals {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
h1{
  border-bottom: 1px solid #ddd;
  display: inline-block;
  padding-bottom: 10px;
}
</style>
