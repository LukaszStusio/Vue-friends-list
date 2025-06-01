<template>
    <form @submit.prevent="submitData" action="" method="" class="">
        <div>
            <label for="name">Name:</label>
            <input type="text" name="name" required v-model="enteredName"/>
        </div>
        <div>
            <label for="surname">Surname:</label>
            <input type="text" name="surname" required v-model="enteredSurname"/>
        </div>
        <div>
            <label for="phone">Phone:</label>
            <input type="tel" name="phone" v-model="enteredPhone"/>
        </div>
        <div>
            <label for="email">E-mail:</label>
            <input type="email" name="email" v-model="enteredEmail"/>
        </div>
        <div>
            <button>Add a friend</button>
        </div>
    </form>
</template>

<script>
    export default {
        emits:['add-contact'],
        data() {
            return {
                enteredName: '',
                enteredSurname: '',
                enteredPhone: '',
                enteredEmail: ''
            }
        },
        methods: {
            submitData () {
                this.$emit('add-contact', this.enteredName, this.enteredSurname, this.enteredPhone, this.enteredEmail);
            }
        }
    }
</script>