<template>
    <div class="card">
        <h2>Add New Contact</h2>
        <form @submit="addFriend">
            <label>Name:</label>
            <input type="text" v-model="name" required><br><br>
            <label>Phone:</label>
            <input type="tel" v-model="phone" required pattern="[0-9]{4} [0-9]{5} [0-9]{2}" placeholder="0123 45678 90"><br><br>
            <label>email:</label>
            <input type="email" v-model="email" required><br><br>
            <button type="reset" @click="cancel">Cancel</button>
            <button type="submit">Add</button>
        </form>
    </div>
</template>

<script>
export default {
    name: "AddFriendContact",
    data() {
        return {
            name: '',
            email: '',
            phone: ''
        }
    },
    methods: {
        cancel() {
            this.resetData()
            this.$emit('changeShowAddFriend')
        },
        addFriend(e) {
            e.preventDefault()
            let id = this.name.split(" ")[0].toLowerCase()
            let friend = {
                id: id,
                name: this.name,
                phone: this.phone,
                email: this.email,
                isFavorite: false
            }
            this.resetData()
            this.$emit('addFriend', friend)
            // FIXME: Implementa este método. Tip utiliza la función de eventos embebido en VueJS
        },
        resetData(){
            this.name = ''
            this.email = ''
            this.phone = ''
        }
    }
}
</script>

<style scoped>

</style>