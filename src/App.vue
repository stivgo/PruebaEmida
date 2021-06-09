<template>
  <section>
    <header><h1>My Friends</h1></header>
    <div class="container">
      <button type="button" @click="addFriend">Add Friend</button>
      <!-- FIXME: Invoca el componente AddFriendContact. Define eventos para adicionar y cancelar. Debe verse este componente solo cuando se oprime el boton Add Friend -->
      <AddFriendContact v-if="showAddFriend" v-on:changeShowAddFriend="cancelAddContact" v-on:addFriend="addContact"/>
    </div>
    <br>
    <ul>
      <!-- FIXME: Lista todos los contactos que hay en la lista friends. 
        Los valores de los atributos deben ser pasados al componente FriendContact
        Tip. Utiliza component props -->
        
      <li v-for="(friend,index) in friends" :key="index">
        <!--FIXME Agrega un botón para eleminar un contacto de la lista de contactos -->
        <FriendContact  v-bind="friend" v-on:changeFavoriteStatus="changeFavoriteStatus"/>
        <button type="button" @click="deleteFriend(index)">Eliminar</button>
      </li>
    </ul>
  </section>
</template>

<script>
/**
 * Para completar este ejericio:
 * 1. Reemplazar todos los FIXME con código para que funcione
 * 2. Crear un nuevo componente para crear un nuevo contacto en la lista de amigos.
 *    El nuevo contacto debe verse reflejado en la lista de este template
 * 3. Crear un boton para eliminar un contacto de la lista de amigos. Crea un mensaje de confiramción para que sea borrado.
 *    Puedes modificar el componente FriendContact para insertar el botón o crearlo en el componente App
 */
import AddFriendContact from './components/AddFriendContact.vue'
import FriendContact from './components/FriendContact.vue'

export default {
  components: {
    //FIXME Define los componentes
    FriendContact,
    AddFriendContact
  },
  data() {
    return {
      friends: [
        {
          id: "manuel",
          name: "Manuel López",
          phone: "0123 45678 90",
          email: "manuel@localhost.com",
          isFavorite: true
        },
        {
          id: "juliana",
          name: "Juliana Gomez",
          phone: "0987 654421 21",
          email: "juliana@localhost.com",
          isFavorite: false
        },
      ],
      showAddFriend: false
    };
  },
  methods: {
    changeFavoriteStatus(friendId) {
      console.log(friendId)
      let index = this.friends.map(f => f.id).indexOf(friendId)
      this.friends[index].isFavorite = !this.friends[index].isFavorite 
      /**
       * FIXME: Este método cambia el estado de favorito al contacto. Llega como argumento el id friend.
       */
    },
    deleteFriend(index) {
      // FIXME: Implementa este método
      this.friends.splice(index,1)
      console.log(index);
    },
    addFriend() {
      this.showAddFriend = !this.showAddFriend
      // FIXME: Implementa este método
    },
    addContact(friend) {
      // FIXME: Implementa este método
      this.friends.push(friend)
      console.log(friend)
      this.addFriend()
    },
    cancelAddContact() {
      this.addFriend()
      // FIXME: Implementa este método
    }
  }
};
</script>

<style>
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

.container {
    text-align: center;
}

.card {
  box-shadow: 0 2px 8px 0 rgba(0,0,0,0.26);
  transition: 0.3s;
  border-radius: 10px;
  width: 90%;
  max-width: 40rem;
  padding: 1rem;
  margin-top: 10px;
  margin: auto;
}

#app ul {
  margin: 0;
  padding: 0;
  list-style: none;
}

#app li {
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
  border-bottom: 4px solid #ccc;
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
  box-shadow: 1px 1px 2px rgba(0, 0, 0, 0.26);
}

#app button:hover,
#app button:active {
  background-color: #ec3169;
  border-color: #ec3169;
  box-shadow: 1px 1px 4px rgba(0, 0, 0, 0.26);
}

</style>