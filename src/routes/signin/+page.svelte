<script lang='ts'>
   
   // Import the functions you need from the SDKs you need
   import { initializeApp } from 'firebase/app';
import firebase from 'firebase/compat/app';
import 'firebase/compat/auth';
import { onMount } from 'svelte';
// TODO: Add SDKs for Firebase products that you want to use
// https://firebase.google.com/docs/web/setup#available-libraries

// Your web app's Firebase configuration
// For Firebase JS SDK v7.20.0 and later, measurementId is optional
const firebaseConfig = {
  apiKey: "AIzaSyAKUJIq6bjpUFSn9krJ9D2cQupN8biIyfw",
  authDomain: "sti-hackathon.firebaseapp.com",
  projectId: "sti-hackathon",
  storageBucket: "sti-hackathon.appspot.com",
  messagingSenderId: "538088055127",
  appId: "1:538088055127:web:117ad676c60ab848ee9e12",
  measurementId: "G-VL922YFEJ1"
};
   
onMount(() => {

            // Initialize Firebase
const app = initializeApp(firebaseConfig);

//const analytics = getAnalytics(app);

let auth = firebase.auth();

  if (auth.currentUser) {
    // The user is already signed in.
  } else {
    // The user is not signed in.
  }
});
    
    async function loginWithGoogle() {
    try {
        firebase.initializeApp(firebaseConfig);
        let auth = firebase.auth();
                // Initialize Firebase

        const provider = new firebase.auth.GoogleAuthProvider();

        await auth.signInWithPopup(provider);
    } catch (e) {
        console.log(e);
    }
  } 
   </script>

<div class={"align-center text-center mt-32"}>
    <h1>Sign into <span class="font-semibold">Rheia</span></h1>
    <br/>
    <button on:click={loginWithGoogle} class='px-2 py-1 bg-blue-600 font-semibold text-white'>Login with Google</button>
</div>

<style>
    h1 {
        font-family: "IBM Plex Sans"
    }
    </style>