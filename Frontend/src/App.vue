<template>
  <div id="app">

    <div class="container main">
  
  <router-view />
    </div>
  </div>
</template>

<script>


export default {
  components: {
  
  },
  computed: {
    currentUser() {
      return this.$store.state.auth.user;
    },
    showAdminBoard() {
      if (this.currentUser && this.currentUser['roles']) {
        return this.currentUser['roles'].includes('ROLE_ADMIN');
      }

      return false;
    },
  },
  methods: {
    logOut() {
      this.$store.dispatch('auth/logout');
      this.$router.push('/login');
    }
  }
};
</script>

<style>
body{
  font-family: 'Lato';
}

#app{
  
  background-color: #fefefe;
}

.main{
    background-color: white;
    padding: 30px 10px;
    border-radius: 15px;
    box-shadow: 0 10px 50px -10px #d6d6d6;
}

</style>