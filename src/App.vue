<template>
  <section>
    <header>
      <h1>My friends</h1>
    </header>
    <new-friend @add-contact="addContact"></new-friend>
    <ul>
      <friend-contact
        v-for="friend in friends"
        :key="friend.id"
        :id="friend.id"
        :friend-name="friend.name"
        :friend-surname="friend.surname"
        :phone-number="friend.phone"
        :email-address="friend.email"
        :is-favorite="friend.isFavorite"
        @toggle-favorite="toggleFavoriteStatus"
        @delete="deleteContact"
      ></friend-contact>
      
    </ul>
  </section>
</template>

<script> 
import NewFriend from './components/NewFriend.vue';
export default {
  components: { NewFriend },
  data() {
    return {
      friends: [
        {
          id: 'manuel',
          name: 'Manuel',
          surname: 'Lorenz',
          phone: '123123123',
          email: 'manuel@localhost.com',
          isFavorite: false
        },
        {
          id: 'julie',
          name: 'Julie',
          surname: 'Jones',
          phone: '456456456',
          email: 'julioe@localhost.com',
          isFavorite: false
        },
        {
          id: 'pedro',
          name: 'Pedro',
          surname: 'Pascal',
          phone: '789789',
          email: 'pedro@localhost.com',
          isFavorite: false
        }
      ]
    };
  },
  methods: {
    toggleFavoriteStatus(friendId) {
      const identifiedFriend = this.friends.find((friend) => friend.id === friendId);
      identifiedFriend.isFavorite = !identifiedFriend.isFavorite;
    },
    addContact(name, surname, phone, email) {
      const newFriendContact = {
        id: new Date().toISOString(),
        name: name,
        surname: surname,
        phone: phone,
        email: email,
        isFavorite: false
      };
      this.friends.push(newFriendContact);
    },
    deleteContact(friendId) {
            this.friends = this.friends.filter(friend => friend.id !== friendId);
        }
  }
}
</script>

<style>
  @import url('https://fonts.googleapis.com/css2?family=Jost&display=swap');
  
* {
    box-sizing: border-box;
  }
  
  html {
    font-family: 'Jost', sans-serif;
  }
  
  body {
    margin: 0;
  }
  
  header {
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
    margin: 3rem auto;
    border-radius: 10px;
    padding: 1rem;
    background-color: #58004d;
    color: white;
    text-align: center;
    width: 90%;
    max-width: 40rem;
  }
  
  #app ul {
    margin: 0;
    padding: 0;
    list-style: none;
  }
  
  #app li,
  #app form {
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
    margin: 1rem auto;
    border-radius: 10px;
    padding: 1rem;
    text-align: center;
    width: 90%;
    max-width: 40rem;
  }
  
  #app h2 {
    font-size: 2rem;
    border-bottom: 4px solid #58004c1c;
    color: #58004d;
    margin: 0 0 1rem 0;
  }
  
  #app button {
    font: inherit;
    cursor: pointer;
    border: 1px solid #ff0077;
    background-color: #ff0077;
    color: white;
    padding: 0.05rem 1rem;
    margin: 0.5rem;
    box-shadow: 1px 1px 2px rgba(0, 0, 0, 0.26);
  }
  
  #app button:hover,
  #app button:active {
    background-color: #ec3169;
    border-color: #ec3169;
    box-shadow: 1px 1px 4px rgba(0, 0, 0, 0.26);
  }
  #app input {
  font: inherit;
  padding: 0.15rem;
  }
  #app label {
    font-weight: bold;
    margin-right: 1rem;
    width: 7rem;
    display: inline-block;
  }
  #app form div {
    margin: 1rem 0;
  }
</style>
