<script>
    // @ts-ignore
    import { Link } from 'svelte-routing';
    let showNavbar = false;
  
    const toggleNavbar = () => {
      showNavbar = !showNavbar;
    };
  </script>

<header class="sticky top-0 z-50">
    <nav class="bg-red-500 border-yellow-200">
      <div class="max-w-screen-xl flex flex-wrap items-center justify-between mx-auto p-4">
        <Link to="/">
          <div class="flex items-center space-x-3">
            <img src="/online-shop.png" class="h-8" alt="SwiftCart Logo" />
            <span class="self-center text-2xl font-semibold whitespace-nowrap text-white">SwiftCart</span>
          </div>
        </Link>
        <button
          on:click={toggleNavbar}
          type="button"
          class="inline-flex items-center p-2 w-10 h-10 justify-center text-sm text-white rounded-lg md:hidden hover:bg-gray-100 focus:outline-none focus:ring-2 focus:ring-gray-200"
          aria-controls="navbar-dropdown"
          aria-expanded={showNavbar}
        >
          <span class="sr-only">Open main menu</span>
          <svg
            class="w-5 h-5"
            aria-hidden="true"
            xmlns="http://www.w3.org/2000/svg"
            fill="none"
            viewBox="0 0 17 14"
          >
            <path
              stroke="currentColor"
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="M1 1h15M1 7h15M1 13h15"
            />
          </svg>
        </button>
