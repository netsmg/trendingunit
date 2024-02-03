<script>
  
  import { page } from "$app/stores";
  import {onAuthStateChanged, signOut} from 'firebase/auth'
  import { fauth } from "../firebase";
  import {onMount} from 'svelte';
  import {userStore} from "../stores/userStore"
  
  
  let me;
onMount(async () => {
    document.title = "Webui | Home";

    onAuthStateChanged(fauth, async (user) => {
      if (user) {
        userStore.set({ ...user, loggedIn: true });
        me = user;
      } else {
        me = false;
        console.log('User Not Logged In!');
        userStore.set({ loggedIn: false });
      }
    });
  });

  let btnClass = 'text-gray-500 dark:text-gray-400 hover:bg-gray-100 dark:hover:bg-gray-700 rounded-lg text-xl p-2';
</script>
<svelte:head>
  
  <link
  rel="stylesheet"
  href="https://cdnjs.cloudflare.com/ajax/libs/animate.css/4.1.1/animate.min.css"
/>

</svelte:head>




      
 



  

  
    <slot />
  
    
  

   




    
  

   



