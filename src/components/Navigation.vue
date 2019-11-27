<template>
    <div>
        <nav class="navbar navbar-expand bg-primary navbar-dark site-nav">
            <div class="container-fluid">
                <router-link to="/" class="navbar-brand">Meeting Log</router-link>
                <div class="navbar-nav ml-auto">
                    <router-link to="/meetings" class="nav-item nav-link">Meetings</router-link>
                    <router-link to="/login" class="nav-item nav-link">Login</router-link>
                    <router-link to="/register" class="nav-item nav-link">Reister</router-link>
                </div>
            </div>
        </nav>
    </div>
</template>