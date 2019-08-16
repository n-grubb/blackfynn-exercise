<template>

    <article class="user">
        <img class="user-photo" :src="user.picture.large" :alt="alt_text" /> 
        <div class="user-details">
            <p class="user-name">{{ user.name.first }} {{ user.name.last }}</p> 
            <address class="user-address">
            {{ user.location.street }}<br />
            {{ user.location.city }}, {{ user.location.state }} {{ user.location.postcode }}
            </address> 
        </div>
    </article>
    
</template>

<script>
export default {
  name: 'UserCard',
  props: {
    user: {
      type: Object,
      required: true
    }
  },
  data() {
    return {
        alt_text: `Profile image for ${this.user.name.first} ${this.user.name.last}`
    }
  }
}
</script>

<style lang="scss">
    .user {
        width: 100%;
        border: 2px solid #e3e3e3;
        border-radius: 4px;
        margin-bottom: .5em;

        display: grid;
        grid-template: auto / 1fr 2fr;

        @media screen and (min-width: 650px) {
            width: 46%;
            margin-right: .5em;
        }

        @media screen and (min-width: 1200px) {
            width: 30%;
            margin-right: .5em;
        }
    }

    .user-photo {
        grid-column: 1;
        width: 100%;
        height: auto;
    }

    .user-details {
        grid-column: 2;
        padding: 0 1em;
        font-size: .75em;
        text-transform: capitalize;

        display: grid;
        align-content: center;
        
    }

    .user-name {
        margin-top: 0;
    }
</style>