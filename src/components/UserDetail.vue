<template>
    <div class="component">
        <h3>You may view the User Details here</h3>
        <p>Many Details</p>
        <p>{{ newName }}</p>
        <p>User Name: {{ switchName() }}</p>
        <p>Age: {{ userAge }}</p>
        <button @click="resetName">Reset Name</button>
        <button @click="resetFN">Reset Name From Parent</button>
    </div>
</template>

<script>
import { eventBus } from '../main.js'

export default {
    //props: ['newName'],
    props: {
        newName: {
            type: String,
            //required: true,
            //default: 'No Name Provided',
            //Number
            //Boolean
            //Function
            //Object
            //Array
        },
        resetFN: Function,
        userAge: Number
    },
    methods: {
        switchName () {
            return this.newName.split('').reverse().join('')
        },
        resetName () {
            this.newName = "Jessen"
            this.$emit('nameWasReset', this.newName)
        }
    },
    created () {
        eventBus.$on('ageWasEdited', (age) => { 
            this.userAge = age;
        })
    }
}
</script>

<style scoped>
    div {
        background-color: lightcoral;
    }
</style>
