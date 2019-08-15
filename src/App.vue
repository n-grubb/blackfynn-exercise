<template>

  <div id="app">
    <header class="site-header">
      <h1>User Directory</h1>
    </header>

    <SearchBar :results="results" @search-user-list="updateUserList"></SearchBar>

    <section class="user-listings">
            
      <article v-for="user in results" :key="user.login.uuid" class="user">
        <img class="user-photo" :src="user.picture.large" /> 
        <div class="user-details">
          <p class="user-name">{{ user.name.first }} {{ user.name.last }}</p> 
          <address class="user-address">
            {{ user.location.street }}<br />
            {{ user.location.city }}, {{ user.location.state }} {{ user.location.postcode }}
          </address> 
        </div>
      </article>

    </section>

  </div>

</template>


<script>
import SearchBar from './components/SearchBar.vue'

const dummy_data = [
  {"gender":"male","name":{"title":"mr","first":"lígio","last":"da cunha"},"location":{"street":"1904 rua carlos gomes","city":"mesquita","state":"maranhão","postcode":22826,"coordinates":{"latitude":"-77.5205","longitude":"-110.4235"},"timezone":{"offset":"+5:30","description":"Bombay, Calcutta, Madras, New Delhi"}},"email":"lígio.dacunha@example.com","login":{"uuid":"a4b32852-807d-4d73-bbbf-5eea8aa1514f","username":"sadzebra407","password":"poland","salt":"GcBZYBmB","md5":"26f389e9493a44f7cda66d3d6efe3f5c","sha1":"a72f280e777d1e5224997f1ca78a1ff285f72245","sha256":"9e89b78f9c5c40ea0a3aaf1685cf74a129659930542a0c373b58b1af717c16dc"},"dob":{"date":"1994-02-04T05:09:49Z","age":25},"registered":{"date":"2017-01-27T14:24:24Z","age":2},"phone":"(56) 6130-2960","cell":"(61) 8954-6398","id":{"name":"","value":null},"picture":{"large":"https://randomuser.me/api/portraits/men/66.jpg","medium":"https://randomuser.me/api/portraits/med/men/66.jpg","thumbnail":"https://randomuser.me/api/portraits/thumb/men/66.jpg"},"nat":"BR"},
  {"gender":"female","name":{"title":"miss","first":"ece","last":"hamzaoğlu"},"location":{"street":"1855 anafartalar cd","city":"diyarbakır","state":"kırıkkale","postcode":38344,"coordinates":{"latitude":"23.5168","longitude":"-156.2205"},"timezone":{"offset":"-12:00","description":"Eniwetok, Kwajalein"}},"email":"ece.hamzaoğlu@example.com","login":{"uuid":"a2ee86a6-fdeb-4670-8214-e561ebfe6ad4","username":"crazytiger980","password":"speed","salt":"yg5R84xQ","md5":"92700b110b56019583a70959cac59e44","sha1":"fd415f69b34ddc86967f2235abf70622d55b2bc1","sha256":"c4b81ae411adbf150807370e60e1122bccf7b490accd6187f998cd257a3193c7"},"dob":{"date":"1994-05-30T16:50:19Z","age":25},"registered":{"date":"2016-08-22T17:45:54Z","age":2},"phone":"(696)-950-9756","cell":"(511)-556-5368","id":{"name":"","value":null},"picture":{"large":"https://randomuser.me/api/portraits/women/9.jpg","medium":"https://randomuser.me/api/portraits/med/women/9.jpg","thumbnail":"https://randomuser.me/api/portraits/thumb/women/9.jpg"},"nat":"TR"},
  {"gender":"male","name":{"title":"mr","first":"simon","last":"christensen"},"location":{"street":"8741 nørrevang","city":"roedovre","state":"hovedstaden","postcode":82303,"coordinates":{"latitude":"69.8252","longitude":"172.2316"},"timezone":{"offset":"0:00","description":"Western Europe Time, London, Lisbon, Casablanca"}},"email":"simon.christensen@example.com","login":{"uuid":"fe1afae9-0fc9-4a82-988a-84ae57d16d9a","username":"crazyrabbit181","password":"electra","salt":"LI1p5TRW","md5":"38fda481bdf55c7de6ddfd6f0e47ad31","sha1":"1bffe2b613e736fb1d6e2ce32cd7281cc0550dd0","sha256":"8729d624cb606eee45681340eac5fec8d9791cf9838cd0155e757104e1baac56"},"dob":{"date":"1948-06-02T04:57:56Z","age":71},"registered":{"date":"2017-02-04T02:30:28Z","age":2},"phone":"52751544","cell":"80387463","id":{"name":"CPR","value":"405566-3770"},"picture":{"large":"https://randomuser.me/api/portraits/men/98.jpg","medium":"https://randomuser.me/api/portraits/med/men/98.jpg","thumbnail":"https://randomuser.me/api/portraits/thumb/men/98.jpg"},"nat":"DK"}
];

export default {
  name: 'app',
  components: {
    SearchBar
  },
  data() {
    return {
      all_users: dummy_data,
      results: dummy_data
    }
  },
  methods: {
    updateUserList( search_string ) {
      console.log('filtering users by string...', search_string );
    }
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
