<template>
    
    <section class="user-listings">
        <ErrorMessage :display="show_error">
            <p>No users found that match that search.<br /> Displaying all users.</p>
        </ErrorMessage>
        <Spinner :show_spinner="show_spinner"></Spinner>
        <UserCard v-for="(user, index) in users" :key="user.login.uuid" :user="user" :index="index"></UserCard>
    </section>

</template>

<script>
import UserCard from './UserCard.vue'
import ErrorMessage from './ErrorMessage.vue'
import Spinner from './Spinner.vue'

export default {
  name: 'UserList',
  components: {
    UserCard,
    ErrorMessage,
    Spinner
  },
  props: {
    users: {
      type: Array,
      required: true
    },
    show_spinner: {
        type: Boolean
    },
    show_error: {
        type: Boolean
    }
  }
}
</script>

<style lang="scss">
    .user-listings {
        padding-top: .5em;
        display: flex;
        flex-wrap: wrap;
        justify-content: flex-start;
        align-items: center;
    }
</style>