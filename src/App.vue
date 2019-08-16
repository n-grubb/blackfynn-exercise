<template>

  <div id="app">
    <header class="site-header">
      <h1>User Directory</h1>
    </header>
    <SearchBar :results="results" @search-user-list="updateUserList"></SearchBar>
    <UserList :users="results" :show_spinner="show_spinner" :show_error="show_error" ></UserList>
  </div>

</template>


<script>
import SearchBar from './components/SearchBar.vue'
import UserList from './components/UserList.vue'

import axios from 'axios';

export default {
  name: 'app',
  components: {
    SearchBar,
    UserList
  },
  data() {
    return {
      all_users: [],
      results: [],
      show_spinner: true,
      show_error: false
    }
  },
  methods: {
    
    updateUserList( search_string ) {

      // filter are users by full name
      this.results = this.all_users.filter( user => {
        var user_full_name = user.name.first + ' ' + user.name.last;
        return user_full_name.includes( search_string.toLowerCase() );
      } );

      // show all users if there is no match, set an error flag to display message
      if ( this.results.length < 1 ) {
        this.results = this.all_users;
        this.show_error = true;
      } else {
        this.show_error = false;
      }

    }

  },
  created() {
    axios.get(`https://randomuser.me/api/?results=100`).then( response => {
      this.all_users = response.data.results;
      this.results   = this.all_users;
      this.show_spinner = false;
    }).catch(e => {
      console.error( e );
    });
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}
</style>
