
 <svelte:head>

  <!-- Plugins CSS Files -->
  <link rel="stylesheet" href="https://demo.themefisher.com/spydea-tailwind/plugins/aos/aos.css" />

  <!-- Fontawesome -->
  <link rel="stylesheet" href="https://demo.themefisher.com/spydea-tailwind/plugins/font-awesome/v6/brands.css" />
  <link rel="stylesheet" href="https://demo.themefisher.com/spydea-tailwind/plugins/font-awesome/v6/regular.css" />
  <link rel="stylesheet" href="https://demo.themefisher.com/spydea-tailwind/plugins/font-awesome/v6/solid.css" />
  <link rel="stylesheet" href="https://demo.themefisher.com/spydea-tailwind/plugins/font-awesome/v6/fontawesome.css" />

  <!-- Main Stylesheet -->
  <link href="https://demo.themefisher.com/spydea-tailwind/styles/main.css" rel="stylesheet" />

</svelte:head>
<div
  class="line-bg fixed left-0 top-1/2 z-10 flex h-screen w-full -translate-y-1/2 justify-between"
>
  <div class="container flex justify-between">
    <span class="inline-block h-full opacity-50 md:opacity-100"></span>
    <span class="inline-block h-full opacity-50 md:opacity-100"></span>
    <span class="inline-block h-full opacity-50 md:opacity-100"></span>
    <span class="inline-block h-full opacity-50 md:opacity-100"></span>
    <span class="inline-block h-full opacity-50 md:opacity-100"></span>
    <span class="inline-block h-full opacity-50 md:opacity-100"></span>
  </div>
</div>
<!-- End background lines -->
<div class="notice">
  <div class="container-fluid">
    <div class="relative flex items-center justify-between sm:text-center">
      <span class="mx-auto pr-10">
        This site is in progress 
        <a href="/">Learn More</a>
      </span>
      <button
        class="notice-close-btn flex h-[20px] min-w-[20px] items-center justify-center rounded-full border-2 border-white text-white opacity-80"
        aria-label="close toast button"
        type="button"
      >
        <i class="fa-solid fa-xmark !text-[10px]"></i>
      </button>
    </div>
  </div>
</div>
<!-- End Top Header  -->

<header
  class="header bg-quaternary/20 z-50"
>
  <nav class="navbar container relative z-30">
    <a href="/" class="navbar-brand"><b style="font-size:large;">
      WEBui</b>
    </a>
    <!-- End logo -->

    <select
      class="language-switcher block border-0 bg-right px-6 pl-0 text-base lg:hidden"
      aria-label="language switcher"
    >
      <option value="bn">Bn</option>
      <option value="en">En</option>
    </select>
    <!-- End Language Switcher -->

    <button
      class="navbar-toggler group relative ml-4"
      aria-label="navbar toggler"
    >
      <div
        class="relative flex h-[30px] w-[30px] transform items-center justify-center overflow-hidden rounded-full ring-0 transition-all duration-200"
      >
        <div
          class="flex h-[15px] w-[18px] origin-center transform flex-col justify-between overflow-hidden transition-all duration-300 group-[.active]:h-[21px]"
        >
          <div
            class="h-[2px] w-7 origin-left transform bg-dark transition-all duration-300 group-[.active]:translate-x-10"
          ></div>
          <div
            class="h-[2px] w-7 transform rounded bg-dark transition-all delay-75 duration-300 group-[.active]:translate-x-10"
          ></div>
          <div
            class="h-[2px] w-7 origin-left transform bg-dark transition-all delay-150 duration-300 group-[.active]:translate-x-10"
          ></div>
          <div
            class="absolute top-2.5 flex w-0 -translate-x-10 transform items-center justify-between transition-all duration-500 group-[.active]:w-12 group-[.active]:translate-x-0"
          >
            <div
              class="absolute h-[2px] w-5 rotate-0 transform bg-dark transition-all delay-300 duration-500 group-[.active]:rotate-45"
            ></div>
            <div
              class="absolute h-[2px] w-5 -rotate-0 transform bg-dark transition-all delay-300 duration-500 group-[.active]:-rotate-45"
            ></div>
          </div>
        </div>
      </div>
    </button>
    <!-- End Navbar Toggler -->

    <div class="navbar-wrapper">
      <ul class="navbar-nav">
        <li class="nav-item">
          <a href="/" class="nav-link">Home</a>
        </li>
        <li class="nav-item">
          <a href="/about" class="nav-link">About</a>
        </li>
        <li class="nav-item">
          <a href="/blog" class="nav-link">Blog</a>
        </li>
        <li class="nav-item nav-dropdown group">
          <span class="nav-link inline-flex items-center">
            Pages
            <i class="fa-solid fa-chevron-down arrow-icon"></i>
          </span>
          <ul
            class="nav-dropdown-list lg:group-hover:visible lg:group-hover:opacity-100"
          >
            <li class="nav-dropdown-item">
              <a href="/" class="nav-dropdown-link">
                Integration
              </a>
            </li>
            <li class="nav-dropdown-item">
              <a href="/" class="nav-dropdown-link">
                Integration Single
              </a>
            </li>
            <li class="nav-dropdown-item">
              <a href="/" class="nav-dropdown-link">Career</a>
            </li>
            <li class="nav-dropdown-item">
              <a href="/" class="nav-dropdown-link">
                Career Single
              </a>
            </li>
            <li class="nav-dropdown-item">
              <a href="/" class="nav-dropdown-link">Pricing</a>
            </li>
            <li class="nav-dropdown-item">
              <a href="/" class="nav-dropdown-link">All Author</a>
            </li>
            <li class="nav-dropdown-item">
              <a href="/" class="nav-dropdown-link">
                Author Single
              </a>
            </li>
            <li class="nav-dropdown-item">
              <a href="/" class="nav-dropdown-link">
                Blog Single
              </a>
            </li>
            <li class="nav-dropdown-item">
              <a href="/contact" class="nav-dropdown-link">Contact</a>
            </li>
            <li class="nav-dropdown-item">
              <a href="/register" class="nav-dropdown-link">Sign up</a>
            </li>
            <li class="nav-dropdown-item">
              <a href="/" class="nav-dropdown-link">
                Terms & Conditions
              </a>
            </li>
            <li class="nav-dropdown-item">
              <a href="/" class="nav-dropdown-link">404</a>
            </li>
          </ul>
        </li>
      </ul>
      <!-- End Navbar Nav -->

      <div
        class="order-2 mx-auto mb-[0.75rem] flex flex-col items-center lg:mx-0 lg:mb-0 lg:ml-7 lg:flex-row"
      >
        <select class="language-switcher hidden lg:block">
          <option value="en">EN</option>
          <option value="bn">Bn</option>
        </select>
        <div
          class="flex flex-col justify-center gap-5 pt-4 text-center lg:ml-7 lg:flex-row lg:gap-7 lg:pt-0 lg:text-left"
        >
          <a
            href="/login"
            class="btn btn-outline-primary w-[200px] min-[340px]:w-[300px] lg:w-auto"
          >
            Login
          </a>
          <a
            href="/blog"
            class="btn btn-primary w-[200px] min-[340px]:w-[300px] lg:w-auto"
          >
            Get Started
          </a>
        </div>
      </div>
    </div>
    <!-- End Navbar Wrapper -->
  </nav>
  <!-- End Main Header  -->

  <div
    class="line-bg  absolute z-20"
  >
    <div class="container flex justify-between">
      <span
        class="bg-line-yellow inline-block h-full opacity-50 md:opacity-100"
      ></span>
      <span
        class="bg-line-yellow inline-block h-full opacity-50 md:opacity-100"
      ></span>
      <span
        class="bg-line-yellow inline-block h-full opacity-50 md:opacity-100"
      ></span>
      <span
        class="bg-line-yellow inline-block h-full opacity-50 md:opacity-100"
      ></span>
      <span
        class="bg-line-yellow inline-block h-full opacity-50 md:opacity-100"
      ></span>
      <span
        class="bg-line-yellow inline-block h-full opacity-50 md:opacity-100"
      ></span>
    </div>
  </div>
  <!-- End background lines -->
</header>
<!-- End Header -->



  
       



