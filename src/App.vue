<template>
  <div>
    <!-- directly embedding the props header in the template -->
    <!-- <Modal header="This is giveaway"/> -->

    <h1>{{title}}</h1>
    <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
    <div>
      <input type="text" ref="name">
      <button @click="handleInputRef">Click Me</button>
    </div>
    <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    <br>
    <div>
      <!-- click.alt makes click method run only if ALt key is pressed with click -->
      <button @click.alt="toggleModal">Show Modal (Need to hold alt key with click)</button>
    </div>

    <div>
      <button @click="toggleModal2">Display Modal 2</button>
    </div>
    <!-- send the components to different parts of DOM -->
    <teleport to=".modals" v-if="showModal">
      <Modal @close="toggleModal" theme="sale" :header="header" :text="text">
        <template v-slot:links>
          <a href="#">Sign up now</a>
          <a href="#">More Info</a>
        </template>
        <p>Model 1</p>
        <hr>
      </Modal>
    </teleport>

    <div v-if="showModal2">
      <Modal @close="toggleModal2" :header="header" :text="text">
          <h2>Here is the sample of the description function that is being used over and over again</h2>
      </Modal>
    </div>
    <hr>
    <SignupForm/>

    
   
  </div>
</template>

<script>
//import HelloWorld from './components/HelloWorld.vue'
import Modal from './components/Modal.vue'
import SignupForm from './components/SignupForm'
          
export default {
  name: 'App',

  components:{
    Modal,
    SignupForm
  },
  // components: {
  //   HelloWorld
  // }
  data(){
    return{
      title: 'My new Vue App :)',
      header:"This is a giveaway",
      text:"Enjoy shopping",
      showModal: false,
      showModal2: false
    }
  },
  methods:{
   handleInputRef(){
     console.log(this.$refs.name);
    //  adding class; js fxn
     this.$refs.name.classList.add('active')
    //  focus input 
     this.$refs.name.focus()
   },
   toggleModal(){
     this.showModal = !this.showModal
   },
   toggleModal2(){
     console.log('showModal2')
     this.showModal2=!this.showModal2
   } 
  }

}
</script>

<style>
#app,.modals {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
h1 {
  border-bottom: 1px solid #ddd;
  display: inline-block;
  padding-bottom: 10px;
}
</style>
