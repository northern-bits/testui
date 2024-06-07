<script>
    import { page } from '$app/stores';
    import { Navbar, NavBrand, NavLi, NavUl, NavHamburger, Button, Input, DarkMode } from 'flowbite-svelte';
    import { SearchOutline } from 'flowbite-svelte-icons';
    import { writable } from 'svelte/store';
    import { SvelteFlow, Background, Controls } from '@xyflow/svelte';
    import '@xyflow/svelte/dist/style.css';
    $: activeUrl = $page.url.pathname;
    let btnClass = 'text-gray-500 dark:text-gray-400 hover:bg-gray-100 dark:hover:bg-gray-700 rounded-lg text-xl p-2';
    let activeClass = 'text-white bg-green-700 md:bg-transparent md:text-green-700 md:dark:text-white dark:bg-green-600 md:dark:bg-transparent';
    let nonActiveClass = 'text-gray-700 hover:bg-gray-100 md:hover:bg-transparent md:border-0 md:hover:text-green-700 dark:text-gray-400 md:dark:hover:text-white dark:hover:bg-gray-700 dark:hover:text-white md:dark:hover:bg-transparent';
    const nodes = writable([]);
    const edges = writable([]);
</script>
  
  <Navbar>
    <NavBrand href="/">
      <!-- <img src="/images/flowbite-svelte-icon-logo.svg" class="me-3 h-6 sm:h-9" alt="Flowbite Logo" /> -->
      <span class="self-center whitespace-nowrap text-xl font-semibold dark:text-white">Flowbite</span>
    </NavBrand>
    <div class="flex md:order-2">
      <Button color="none" data-collapse-toggle="mobile-menu-3" aria-controls="mobile-menu-3" aria-expanded="false" class="md:hidden text-gray-500 dark:text-gray-400 hover:bg-gray-100 dark:hover:bg-gray-700 focus:outline-none focus:ring-4 focus:ring-gray-200 dark:focus:ring-gray-700 rounded-lg text-sm p-2.5 me-1">
        <SearchOutline class="w-5 h-5" />
      </Button>
      <div class="hidden relative md:block">
        <div class="flex absolute inset-y-0 start-0 items-center ps-3 pointer-events-none">
          <SearchOutline class="w-4 h-4" />
        </div>
        <Input id="search-navbar" class="ps-10" placeholder="Search..." />
      </div>
      <NavHamburger />
    </div>
    <NavUl>
      <NavLi href="/" active={true}>Home</NavLi>
      <NavLi href="/about">About</NavLi>
      <NavLi href="/docs/components/navbar">Navbar</NavLi>
      <DarkMode {btnClass} />
    </NavUl>
  </Navbar>
  <main>
    <div class="flex justify-center items-center h-96 m-2">
        <SvelteFlow {nodes} {edges}>
        <Background />
        <Controls />
        </SvelteFlow>
    </div>
  </main>
  
  <style>
    main {
      height: 100vh;
    }
  </style>
  