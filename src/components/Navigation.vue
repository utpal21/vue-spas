<template>
    <div>
        <nav class="navbar navbar-expand bg-primary navbar-dark site-nav">
            <div class="container-fluid">
                <router-link to="/" class="navbar-brand">Meeting Log</router-link>
                <div class="navbar-nav ml-auto">
                    <router-link v-if="user" to="/meetings" class="nav-item nav-link">Meetings</router-link>
                    <router-link v-if="!user" to="/login" class="nav-item nav-link">Login</router-link>
                    <router-link v-if="!user" to="/register" class="nav-item nav-link">Reister</router-link>
                    <button v-if="user" class="nav-btn btn nav-link" @click="$emit('logout')">Logout</button>
                </div>
            </div>
        </nav>
    </div>
</template>
<script>
export default {
    name: "navigation",
    props: ['user']
}
</script>