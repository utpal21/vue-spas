<template>
  <div id="app"> 
    <Navigation :user="user" @logout="logout" />
    <router-view class="container" :user="user" @logout="logout" @addMeeting="addMeeting"/>
  </div>
</template>

<script>
import Navigation from "@/components/Navigation.vue";
import Firebase from "firebase";
import db from "./db.js";
export default {
  name: "App",
  data: function() {
    return {
      user: null
    };
  },
  methods: {
    logout: function(){
      Firebase.auth().signOut()
      .then(()=>{
        this.user = null;
        this.$router.push("login");
      });
    },
    addMeetin: function(payload){
      db.collection('users')
      .doc(this.user.uid)
      .collection('meetings')
      .add({
        name: payload,
        createdAt: Firebase.firestore.FieldValue.serverTimestamp(),

      });

    }
  },
  mounted() {
    Firebase.auth().onAuthStateChanged(user => {
      if(user) {
        this.user = user;
      }

    })

    db.collection("users")
      .doc("YIYwaFvSdQ4Jiv5YV0cl")
      .get()
      .then(snapshot => {
        this.user = snapshot.data().name;
      });
  },
  components: {
    Navigation
  }
};
</script>

<style lang="scss">
$primary: #05b2dd;
@import "node_modules/bootstrap/scss/bootstrap";
</style>
