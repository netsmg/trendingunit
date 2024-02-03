<script>
  import { getAuth, createUserWithEmailAndPassword } from 'firebase/auth';
  import { fauth } from "../../firebase"; 
  import { goto } from '$app/navigation';
  
  let email = '';
  let password = '';

  function signUp() {
    createUserWithEmailAndPassword(fauth, email, password)
      .then((userCredential) => {
        const user = userCredential.user;
        console.log('User signed up:', user);
        goto('/login');
      })
      .catch((error) => {
        const errorCode = error.code;
        const errorMessage = error.message;
        console.error(`Sign-up error (${errorCode}): ${errorMessage}`);
      });
  }
  export let year = new Date().getFullYear();
</script>


  <head>
    <meta charset="utf-8" />
    <title>Register | Webui</title>
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <meta content="An authentic blog ui" name="description" />
    <meta content="Netsmg" name="author" />
    
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

  <body>
    <div class="account-pages my-5 pt-sm-5">
      <div class="container">
        <div class="row justify-content-center">
          <div class="col-md-8 col-lg-6 col-xl-5">
            <div class="text-center mb-4">
              
              
              <h4>Sign up</h4>
              <p class="text-muted mb-4">Get your Webui account now.</p>
            </div>

            <div class="card">
              <div class="card-body p-4">
                <div class="p-3">
                  <form>
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
                          aria-describedby="basic-addon5"bind:value={email} required
                        />
                      </div>
                    </div>

                    <div class="mb-3">
                      <label class="form-label">Username</label>
                      <div class="input-group bg-light-subtle mb-3 rounded-3">
                        <span class="input-group-text border-light text-muted" id="basic-addon6">
                          <i class="ri-user-2-line"></i>
                        </span>
                        <input
                          type="text"
                          class="form-control form-control-lg bg-light-subtle border-light"
                          placeholder="Enter Username"
                          aria-label="Enter Username"
                          aria-describedby="basic-addon6"
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

                    <div class="d-grid">
                      <button class="btn btn-primary waves-effect waves-light" type="submit" on:click={signUp}>
                        Sign up
                      </button>
                    </div>

                    <div class="mt-4 text-center">
                      <p class="text-muted mb-0">
                        By registering you agree to the Webui
                        <a href="/" class="text-primary">
                          Terms of Use
                        </a>
                      </p>
                    </div>
                  </form>
                </div>
              </div>
            </div>

            <div class="mt-5 text-center">
              <p>
                Already have an account ?{" "}
                <a href="./login" class="fw-medium text-primary">
                  Signin
                </a>{" "}
              </p>
              <p>&copy; {year} Webui. </p>
            </div>
          </div>
        </div>
      </div>
    </div>
    <!-- end account-pages -->

    <!-- JAVASCRIPT -->
  </body>
