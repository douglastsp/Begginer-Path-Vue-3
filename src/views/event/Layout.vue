<template>
    <div v-if="event">
        <h1>{{ event.title }}</h1>
        <div id="nav">
            <router-link :to="{ name: 'EventDetails'}">Details</router-link> |
            <router-link :to="{ name: 'EventRegister'}">Register</router-link> |
            <router-link :to="{ name: 'EventEdit'}">Edit</router-link>
        </div>
    </div>
    <router-view :event="event" />
</template>

<script>
import EventService from '@/services/EventService.js'

export default {
    props: ['id'],

    data() {
        return {
            event: null,
        }
    },

    created() {
        //fetch event by id and set a local data
        EventService.getEvent(this.id)
            .then(response => {
                console.log(response.data)
                this.event = response.data
            })
            .catch(error => {
                console.log(error)
            })
    }
}
</script>
