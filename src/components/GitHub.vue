<template>
  <div class="github">

    <h1>Listagem de Usuários</h1>

    <input v-model="username" type="text">
    <button @click="search">Buscar</button>

    <div class="users">
      <span v-for="user in users" :key="user.id">
        <p>
          Login: {{ user.login }}
        </p>

        <img :src="user.avatar_url">
        
        <p><a @click="repo(user.login)">
          Repositórios
        </a></p>
      </span>
    </div>

  </div>
</template>

<script>
  import axios from 'axios';

  export default {
    name: 'GitHub',

    data() {
      return {
        username: '',
        users: [],
      };
    },

    methods: {
      search: function () {
        if (this.username) {
          let url = 'https://api.github.com/search/users?q=' + this.username;

          axios.get(url).then((response) => {
            this.users = response.data.items;
          }).catch((message) => {
            alert(message);
          });
        }
      },

      repo: function (login) {
        const url = `https://github.com/${login}?tab=repositories`;
        window.open(url, '_blanck')
      }
    },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  a {
    color: #42b983;
    cursor: pointer;
  }
</style>