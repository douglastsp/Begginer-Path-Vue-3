<template>
    <div>
        <p>Register the event here</p>
        <button @click="register">Register Me</button> 
    </div>
</template>

<script>

export default {
    props: ['event'],
    methods: {
        register() {
            // Call to API
            //If registered then redirect to event details
            this.$router.push({
                name: 'EventDetails'
            })
        }
    }
}
</script>