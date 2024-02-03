<script>
  import { Navbar, NavBrand, Dropdown, DropdownItem, DropdownHeader, Chevron } from "flowbite-svelte";
  import Icon from "@iconify/svelte";
  import { page } from "$app/stores";
  import {onAuthStateChanged, signOut} from 'firebase/auth'
  import { fauth } from "../firebase";
  import {onMount} from 'svelte';
  import {userStore} from "../stores/userStore"
  import toast, { Toaster } from 'svelte-french-toast';
  
  let me;
  onMount(async () => {
    document.title = "Webui | Home";
   const  saveSettings =() => {
      return new Promise((resolve, reject) => {
        let x = setInterval(()=>{
          if($userStore.loggedIn===true){
          resolve();
          clearInterval(x);
        }else if($userStore.loggedIn===false){
          reject();
          clearInterval(x);
        }
        }, 100)
      });
    }
    toast.promise(
        saveSettings(),
        {
          loading: 'Checking...',
          success: 'Signed In!',
          error: 'You are not signed In!',
        },
    );
    onAuthStateChanged(fauth, async(user) => {
        if(user) {
            userStore.set({...user, loggedIn: true});
            me = user;
        } else{
           me = false
            console.log('User Not Logged In!');
            userStore.set({loggedIn: false});
        }
       
    });
  
  });

  

  const openSide = () => {
    // console.log("sideOpen");
    sideOpen = !sideOpen;
  };
  $: open = sideOpen;

  const logOut = async() =>{
      try {
          await signOut(fauth);
      } catch (err) {
        console.log(err);
      }
  }
  let btnClass = 'text-gray-500 dark:text-gray-400 hover:bg-gray-100 dark:hover:bg-gray-700 rounded-lg text-xl p-2';
</script>
<svelte:head>
  
  <link
  rel="stylesheet"
  href="https://cdnjs.cloudflare.com/ajax/libs/animate.css/4.1.1/animate.min.css"
/>

</svelte:head>
<Toaster/>


<Navbar
  navClass="sticky top-0 flex justify-between items-center shadow-sm p-1 font-hind bg-clip-padding backdrop-filter backdrop-blur-sm bg-opacity-5 dark:bg-opacity-20 border-1 border-gray-100 z-[99]"
  let:hidden
  let:toggle
>
  <NavBrand>
    <div class="flex items-center md:hidden">
      <button on:click={openSide} class="lg:hidden btn btn-sm mr-4">
        <span>
          <svg viewBox="0 0 100 80" class="fill-token w-4 h-4">
            <rect
              rx="10px"
              ry="10px"
              stroke-linejoin="round"
              width="100"
              height="20"
            />
            <rect
              rx="10px"
              ry="10px"
              stroke-linejoin="round"
              y="30"
              width="100"
              height="20"
            />
            <rect
              rx="10px"
              ry="10px"
              stroke-linejoin="round"
              y="60"
              width="100"
              height="20"
            />
          </svg>
        </span>
      </button>
    </div>

    <span
      class="max-sm:text-[17px] self-center whitespace-nowrap text-xl font-bold font-poppins dark:text-blue-600 text-blue-500"
    >
      Webui
    </span>
    <DarkMode {btnClass} />
  </NavBrand>
 
  {#if me}
  <Chevron aligned><div><img class="w-[30px] h-[30px] rounded-full s-nb_ptBq0IalQ" src={me.photoURL} alt="Rounded avatar"></div></Chevron>
  <Dropdown>
    <DropdownHeader>{me.displayName}</DropdownHeader>
    <DropdownItem><div class="flex justify-between items-center"><div class="flex gap-1 items-center"><Icon icon="mdi:theme-light-dark" /> Theme</div> <DarkMode {btnClass} /></div></DropdownItem>
    <DropdownItem slot="footer" on:click={logOut}>Sign out</DropdownItem>
  </Dropdown>
  {:else}
  <div class="flex gap-2 items-center">
  <a href="/auth"><button type="button" class="btn variant-soft-primary max-sm:btn-sm">
    <span><Icon icon="bi:google" /></span>
    <span>Sign In</span>
  </button></a>
</div>
  {/if}
 

</Navbar>


  

  
    <slot />
  
    
  

   




    
  

   



