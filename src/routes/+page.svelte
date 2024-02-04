

<script>
  import { onMount } from 'svelte';
  import { fauth } from "../firebase";
  import { getAuth, signInWithEmailAndPassword, createUserWithEmailAndPassword } from 'firebase/auth';
  import { goto } from '$app/navigation';
import toast, { Toaster } from 'svelte-french-toast';

import {userStore} from "../stores/userStore"
  const auth = getAuth();
  let email = '';
  let password = '';
  let isSignIn = true;

  onMount(async () => {
    document.title = "Webui | Home";
    
    const saveSettings = () => new Promise((resolve, reject) => {
      let x = setInterval(() => {
        if ($userStore.loggedIn === true) {
          resolve();
          clearInterval(x);
        } else if ($userStore.loggedIn === false) {
          reject();
          clearInterval(x);
        }
      }, 100);
    });

    toast.promise(
      saveSettings(),
      {
        loading: 'Checking...',
        success: 'Signed In!',
        error: 'You are not signed In!',
      },
    );

    onAuthStateChanged(fauth, async(user) => {
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

  function handleAuthentication(action) {
    action(auth, email, password)
      .then((userCredential) => {
        const user = userCredential.user;
        console.log(`${isSignIn ? 'Signed in' : 'Signed up'} user:`, user);
        goto('/blog');
      })
      .catch((error) => {
        const errorCode = error.code;
        const errorMessage = error.message;
        console.error(`${isSignIn ? 'Sign-in' : 'Sign-up'} error (${errorCode}): ${errorMessage}`);
      });
  }

  function toggleForm() {
    isSignIn = !isSignIn;
  }

  export let year = new Date().getFullYear();
</script>

<!-- Rest of your HTML structure remains unchanged -->
<head>
    <meta charset="utf-8" />
    <title>Log in | Webui</title>
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <meta content="Responsive Bootstrap 5 Chat App" name="description" />
    <meta content="Netsmg" name="author" />
    <!-- App favicon -->
    
    <link
      href="https://cdn.jsdelivr.net/npm/remixicon@2.3.0/fonts/remixicon.css"
      rel="stylesheet"
    />
    <link href="./css/bootstrap.min.css" id="bootstrap-style" rel="stylesheet" type="text/css" />
    <!-- Icons Css -->
    <link href="./css/icons.min.css" rel="stylesheet" type="text/css" />
    <!-- App Css-->
    <link href="./css/app.min.css" id="app-style" rel="stylesheet" type="text/css" />
  </head>
<div class="account-pages my-5 pt-sm-5">
  <div class="container">
    <div class="row justify-content-center">
      <div class="col-md-8 col-lg-6 col-xl-5">
<div class="text-center mb-4">
              
              <h4>Sign in</h4>
              <p class="text-muted mb-4">Sign in to continue to Webui.</p>
            </div>
        <div class="p-3">
          <form>
            <!-- Email and Password input fields... -->
            <div class="mb-3">
              <label class="form-label">Email</label>
              <div class="input-group bg-light-subtle rounded-3 mb-3">
                <span class="input-group-text text-muted" id="basic-addon5">
                  <i class="ri-mail-line"></i>
                </span>
                <input
                  type="email"
                  class="form-control form-control-lg bg-light-subtle border-light"
                  placeholder="Enter Email"
                  aria-label="Enter Email"
                  aria-describedby="basic-addon5" bind:value={email} required
                />
              </div>
            </div>

            <div class="mb-4">
              <label class="form-label">Password</label>
              <div class="input-group bg-light-subtle mb-3 rounded-3">
                <span class="input-group-text border-light text-muted" id="basic-addon7" >
                  <i class="ri-lock-2-line"></i>
                </span>
                <input
                  type="password"
                  class="form-control form-control-lg bg-light-subtle border-light"
                  placeholder="Enter Password"
                  aria-label="Enter Password"
                  aria-describedby="basic-addon7" bind:value={password} required
                />
              </div>
            </div>

            {#if isSignIn}
              <!-- Sign-in form -->
              <div class="d-grid">
                <button class="btn btn-primary waves-effect waves-light" type="submit" on:click={() => handleAuthentication(signInWithEmailAndPassword)}>
                  Sign in
                </button>
              </div>
            {:else}
              <!-- Sign-up form -->
              <div class="d-grid">
                <button class="btn btn-primary waves-effect waves-light" type="submit" on:click={() => handleAuthentication(createUserWithEmailAndPassword)}>
                  Sign up
                </button>
              </div>
            {/if}

            <!-- Toggle between Sign-in and Sign-up forms -->
            <div class="text-center mt-3">
              <button type="button" class="btn btn-link text-muted" on:click={toggleForm}>
                {#if isSignIn}
                  <div class="mt-5 text-center">
                    Don't have an account? Sign up
                    <p>&copy; {year} Webui. </p>
                  </div>
                {:else}
 
                      
                  <div class="mt-5 text-center">
<p class="text-muted mb-0">
                        By registering you agree to the Webui
                        <a href="/" class="text-primary">
                          Terms of Use
                        </a>
                      </p>
                    <p>
                      Already have an account?
                    </p>
                    <p>&copy; {year} Webui. </p>
                  </div>
                {/if}
              </button>
            </div>
          </form>
        </div>

      </div>
    </div>
  </div>
</div>




   



