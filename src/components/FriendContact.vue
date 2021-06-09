<template>
  <div>
    <h2>{{name}}
      <small v-if="isFavorite"><!-- FIXME el mensaje Favorite debe aparecer si el contacto es favorito --> (Favorite)</small>
    </h2>
    <button @click="toggleFavorite(id)">Toggle Favorite</button>
    <button @click="toggleDetails">Show Details</button>
    <ul v-if="detailsAreVisible">
      <li>
        <strong>Phone: {{phone}}</strong>

      </li>
      <li>
        <strong>Email: {{email}}</strong>

      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "FriendContact",
  props: [
    'id',
    'name',
    'phone',
    'email',
    'isFavorite'
  ],
  data() {
    return {
      detailsAreVisible: false
    };
  },
  methods: {
    toggleDetails() {
      this.detailsAreVisible = !this.detailsAreVisible
    },
    toggleFavorite(id) {
      // FIXME: Implementa este método
      this.$emit('changeFavoriteStatus', id)
    }
  }
};
</script>