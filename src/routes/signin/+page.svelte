<script lang='ts'>
   
   // Import the functions you need from the SDKs you need
import { initializeApp } from "firebase/app";
import { getAnalytics } from "firebase/analytics";
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

// Initialize Firebase
const app = initializeApp(firebaseConfig);
const analytics = getAnalytics(app);


async function loginWithGoogle() {
    try {
      const provider = new firebase.auth.GoogleAuthProvider();

      await firebase.auth().signInWithPopup(provider);
    } catch (e) {
      console.log(e);
    }
  }
   </script>

<h1>
    
    <h1 />

<style>
    h1 {
        font-family: "IBM Plex Sans"
    }
    </style>