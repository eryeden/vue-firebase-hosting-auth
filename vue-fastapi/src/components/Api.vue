<script>

import { getAuth, onAuthStateChanged } from "firebase/auth";

export default {
    name: "Api",
    props: {
        msg: String,
    },
    data() {
        return {
            text: null,
            user_name: "",
            user_id: ""
        }
    },
    mounted() {
        const auth = getAuth();
/*         const user = auth.currentUser;
        if (user !== null) {
            // The user object has basic properties such as display name, email, etc.
            const displayName = user.displayName;
            const email = user.email;
            const photoURL = user.photoURL;
            const emailVerified = user.emailVerified;
            // The user's ID, unique to the Firebase project. Do NOT use
            // this value to authenticate with your backend server, if
            // you have one. Use User.getToken() instead.
            const uid = user.uid;
            this.user_id = uid;
            this.user_name = displayName;
            console.log("User data:" + this.user_id);
        } else {
            console.log("Failed to fetch the user data.");
        } */

        onAuthStateChanged(auth, (user) => {
            if (user) {
                // The user object has basic properties such as display name, email, etc.
                const displayName = user.displayName;
                const email = user.email;
                const photoURL = user.photoURL;
                const emailVerified = user.emailVerified;
                // The user's ID, unique to the Firebase project. Do NOT use
                // this value to authenticate with your backend server, if
                // you have one. Use User.getToken() instead.
                const uid = user.uid;
                this.user_id = uid;
                this.user_name = displayName;
                console.log("User data:" + this.user_id);
            } else {
                // User is signed out
                // ...
                console.log("Failed to fetch the user data.");
            }
        });

    },
    methods: {
    },
}

</script>


<template>
    <h3>User specific data</h3>
    <br />
    <h4>User name: {{ user_name }}</h4>
    <br />
    <h4>User id: {{ user_id }}</h4>
</template>
