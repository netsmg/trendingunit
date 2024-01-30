<script>
  let password = "";

  function unlockScreen() {
    if (password === "123456") {
      // Redirect to homepage if password matches
      window.location.href = "/"; // Change the path accordingly
    } else {
      // Handle incorrect password logic here
      console.log("Incorrect password. Please try again.");
    }
  }
</script>

 <link href="https://cdn.jsdelivr.net/npm/remixicon@2.3.0/fonts/remixicon.css" rel="stylesheet">
        <link href="./css/bootstrap.min.css" id="bootstrap-style" rel="stylesheet" type="text/css" />
        <!-- Icons Css -->
        <link href="./css/icons.min.css" rel="stylesheet" type="text/css" />
        <!-- App Css-->
        <link href="./css/app.min.css" id="app-style" rel="stylesheet" type="text/css" />
<div class="account-pages my-5 pt-sm-5">
  <div class="container">
    <div class="row justify-content-center">
      <div class="col-md-8 col-lg-6 col-xl-5">
        <div class="text-center mb-4">
          

          <h4>Lock screen</h4>
          <p class="text-muted mb-4">Enter your password to unlock the screen!</p>
        </div>

        <div class="card">
          <div class="card-body p-4">
            <div class="p-3">
              <div class="user-thumb text-center mb-4">
                <img src="https://themesbrand.com/chatvia/layouts/assets/images/users/avatar-1.jpg" class="rounded-circle img-thumbnail avatar-lg" alt="thumbnail">
                <h5 class="font-size-15 mt-3">Patricia Smith</h5>
              </div>
              <form on:submit|preventDefault={unlockScreen}>
                <div class="mb-4">
                  <label class="form-label">Password</label>
                  <div class="input-group bg-light-subtle rounded-3 mb-3">
                    <span class="input-group-text text-muted" id="basic-addon2">
                      <i class="ri-lock-2-line"></i>
                    </span>
                    <input bind:value={password} type="password" class="form-control form-control-lg bg-light-subtle" placeholder="Enter Password" aria-label="Enter Password" aria-describedby="basic-addon2">
                  </div>
                </div>

                <div class="d-grid">
                  <button class="btn btn-primary waves-effect waves-light" type="submit">Unlock</button>
                </div>
              </form>
            </div>
          </div>
        </div>

        <div class="mt-5 text-center">
          <p>Not you? Return <a href="./login" class="fw-medium text-primary">Signin</a></p>
          <p>&copy; <script>document.write(new Date().getFullYear())</script> Chatweb.</p>
        </div>
      </div>
    </div>
  </div>
</div>
