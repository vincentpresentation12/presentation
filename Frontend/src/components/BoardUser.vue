<template>
  <div class="container">
    <header class="jumbotron">
      <h3>{{ content }}</h3>
      <router-link to="/modifuser">Editer son profil</router-link><br/>
    </header>
  </div>
</template>

<script>
import UserService from "../services/user.service";

export default {
  nom: "User",
  data() {
    return {
      content: "",
    };
  },
  mounted() {
    UserService.getUserBoard().then(
      (response) => {
        this.content = response.data;
      },
      (error) => {
        this.content =
          (error.response &&
            error.response.data &&
            error.response.data.message) ||
          error.message ||
          error.toString();
      }
    );
  },
};
</script>