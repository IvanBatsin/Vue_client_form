<template>
  <div id="app">
    <ClientForm @openModal="openModal"/>
    <UserInfo 
      v-if="(showModal && userInfo)" 
      @closeModal="closeModal"
      :userInfo="userInfo"
    />
  </div>
</template>

<script>
import ClientForm from './components/Form';
import UserInfo from './components/UserInfo';

export default {
  name: 'App',

  data(){
    return {
      userInfo: undefined,
      showModal: false
    }
  },

  methods: {
    closeModal(){
      this.showModal = false;
    },

    openModal(formData){
      this.userInfo = formData;
      this.showModal = true;
    }
  },

  components: {
    ClientForm, UserInfo
  }
}
</script>

<style lang="scss">
  @import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;500;700&display=swap');

  * {
    padding: 0;
    margin: 0;
    box-sizing: border-box;
  }

  body {
    font-family: 'Roboto', sans-serif;
    background-color: #0872d6;
  }

  #app {
    display: flex;
    justify-content: flex-start;
    flex-direction: column;
    align-items: center;
    width: 80%;
    min-height: 100vh;
    margin: 0 auto;

    @media screen and (max-width:800px) {
      width: 95%;
    }
  }
</style>