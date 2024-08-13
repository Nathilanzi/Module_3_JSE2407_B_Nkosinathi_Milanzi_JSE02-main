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
  
        <div class={`w-full md:block md:w-auto ${showNavbar ? '' : 'hidden'}`} id="navbar-dropdown">
          <ul class="flex flex-col mt-4 border border-gray-100 rounded-lg bg-gray-500 md:space-x-8 md:flex-row md:mt-0 md:border-0 p-4 md:p-0">
            <li>
              <Link
                to="/wishlist"
                class="block py-2 px-3 text-white rounded hover:bg-gray-100 md:hover:bg-transparent md:border-0 md:hover:text-blue-700"
              >
                Wishlist
              </Link>
            </li>
            <li class="relative hidden md:block lg:block">
              <div class="absolute left-3 top-0">
                <p class="flex h-2 w-2 items-center justify-center rounded-full bg-red-500 p-3 text-xs text-white">2</p>
              </div>
              <Link to="/cart" class="text-white hover:bg-gray-700">
                <svg
                  xmlns="http://www.w3.org/2000/svg"
                  fill="none"
                  viewBox="0 0 24 24"
                  stroke-width="1.5"
                  stroke="currentColor"
                  class="h-6 w-6 stroke-white cursor-pointer"
                >
                  <path
                    stroke-linecap="round"
                    stroke-linejoin="round"
                    d="M2.25 3h1.386c.51 0 .955.343 1.087.835l.383 1.437M7.5 14.25a3 3 0 00-3 3h15.75m-12.75-3h11.218c1.121-2.3 2.1-4.684 2.924-7.138a60.114 60.114 0 00-16.536-1.84M7.5 14.25L5.106 5.272M6 20.25a.75.75 0 11-1.5 0 .75.75 0 011.5 0zm12.75 0a.75.75 0 11-1.5 0 .75.75 0 011.5 0z"
                  />
                </svg>
              </Link>
            </li>
            <li class="lg:hidden md:hidden">
              <Link to="/cart" class="block py-2 px-3 text-white rounded hover:bg-gray-100 md:hover:bg-transparent md:border-0 md:hover:text-blue-700">
                Cart
              </Link>
            </li>
            <li>
              <Link
                to="/login"
                class="block py-2 px-3 text-white rounded hover:bg-gray-100 md:hover:bg-transparent md:border-0 md:hover:text-blue-700"
              >
                Login
              </Link>
            </li>
          </ul>
        </div>
      </div>
    </nav>
  </header>

  <style>
    :global(.sticky) {
      position: sticky;
    }
  
    :global(.top-0) {
      top: 0;
    }
  
    :global(.z-50) {
      z-index: 50;
    }
  </style>