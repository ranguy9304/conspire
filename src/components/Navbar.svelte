<script>
  import { onMount, onDestroy } from 'svelte';
  let sidebar_open = false;

  onMount(() => {
    // Listener to open sidebar when mouse touches the left edge of the screen
    window.addEventListener('mousemove', handleMouseMove);
    return () => {
      // Cleanup the listener when the component is destroyed
      window.removeEventListener('mousemove', handleMouseMove);
    };
  });

  function handleMouseMove(event) {
    if (event.clientX < 10 && !sidebar_open) {
      sidebar_open = true; // Open the sidebar if mouse is within 10px of the left edge
    } else if (sidebar_open && (event.clientX > 250)) { // Assuming sidebar width is 250px
      sidebar_open = false; // Close the sidebar if mouse is not over the sidebar
    }
  }
  function toggleSidebar() {
    sidebar_open = !sidebar_open;
    
    // rotate the svg by 180deg
    
    }
    
  // $: sidebarTransform = sidebar_open ? 'translate-x-0' : '-translate-x-full';
</script>

<!-- use tailwind -->


<nav class="bg-black min-w-full flex items-center justify-between p-4 border-b-2 border-gray-500 sticky top-0 z-50">
    <button class="flex-shrink-0 transform transition-transform duration-300" on:click={toggleSidebar} class:rotate-180={sidebar_open}>
        <svg width="24" height="24" xmlns="http://www.w3.org/2000/svg" fill-rule="evenodd" clip-rule="evenodd"><path d="M12 0c-6.623 0-12 5.377-12 12s5.377 12 12 12 12-5.377 12-12-5.377-12-12-12zm0 1c-6.071 0-11 4.929-11 11s4.929 11 11 11 11-4.929 11-11-4.929-11-11-11zm4.828 11.5l-4.608 3.763.679.737 6.101-5-6.112-5-.666.753 4.604 3.747h-11.826v1h11.828z"/></svg>
    </button>
    <div class="flex-grow"></div>
    <h1 class="text-2xl logo" data-text="CONSPIRE">CONSPIRE</h1>
    <div class="flex-grow"></div>
    <div class="flex-shrink-0"></div>
</nav>
<div class="fixed inset-0 bg-black bg-opacity-50 z-40 backdrop-blur-sm transition-opacity duration-300" style="opacity: {sidebar_open ? '1' : '0'}; pointer-events: {sidebar_open ? 'auto' : 'none'};"></div> 
<!-- {#if sidebar_open} -->
<!-- <div class="fixed inset-0 bg-black bg-opacity-50 z-40 backdrop-blur-sm"></div>  -->


<!-- SIDE BAR STARTS -->
 
<aside class="fixed top-0 left-0 z-40 w-64 h-screen bg-black border-r-2 transition-transform duration-300" style="transform: {sidebar_open ? 'translateX(0)' : 'translateX(-100%)'};" aria-label="Sidebar">
  <div class="h-full px-3 py-4 overflow-y-auto bg-black border-r-2 ">
     
     <ul class="space-y-2 font-medium mt-14">
        <li>
           <a href="/" class="flex items-center p-2   group text-white border-l-2 border-white rounded-lg bg-gray-950 hover:bg-gray-700">
              <svg class="w-5 h-5 text-white transition duration-75  group-hover:text-white" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" fill="currentColor" viewBox="0 0 22 21">
                 <path d="M16.975 11H10V4.025a1 1 0 0 0-1.066-.998 8.5 8.5 0 1 0 9.039 9.039.999.999 0 0 0-1-1.066h.002Z"/>
                 <path d="M12.5 0c-.157 0-.311.01-.565.027A1 1 0 0 0 11 1.02V10h8.975a1 1 0 0 0 1-.935c.013-.188.028-.374.028-.565A8.51 8.51 0 0 0 12.5 0Z"/>
              </svg>
              <span class="ms-3">Dashboard</span>
           </a>
        </li>
        <li>
           <a href="/feed" class="flex items-center p-2   dark:text-white  dark:hover:bg-gray-700 group  text-white border-l-2 border-white rounded-lg bg-gray-950 hover:bg-gray-700">
              <svg class="flex-shrink-0 w-5 h-5 text-gray-500 transition duration-75 dark:text-gray-400 group-hover:text-gray-900 dark:group-hover:text-white" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" fill="currentColor" viewBox="0 0 18 18">
                 <path d="M6.143 0H1.857A1.857 1.857 0 0 0 0 1.857v4.286C0 7.169.831 8 1.857 8h4.286A1.857 1.857 0 0 0 8 6.143V1.857A1.857 1.857 0 0 0 6.143 0Zm10 0h-4.286A1.857 1.857 0 0 0 10 1.857v4.286C10 7.169 10.831 8 11.857 8h4.286A1.857 1.857 0 0 0 18 6.143V1.857A1.857 1.857 0 0 0 16.143 0Zm-10 10H1.857A1.857 1.857 0 0 0 0 11.857v4.286C0 17.169.831 18 1.857 18h4.286A1.857 1.857 0 0 0 8 16.143v-4.286A1.857 1.857 0 0 0 6.143 10Zm10 0h-4.286A1.857 1.857 0 0 0 10 11.857v4.286c0 1.026.831 1.857 1.857 1.857h4.286A1.857 1.857 0 0 0 18 16.143v-4.286A1.857 1.857 0 0 0 16.143 10Z"/>
              </svg>
              <span class="flex-1 ms-3 whitespace-nowrap">Kanban</span>
              <span class="inline-flex items-center justify-center px-2 ms-3 text-sm font-medium text-gray-800 bg-gray-100 rounded-full dark:bg-gray-700 dark:text-gray-300">Pro</span>
           </a>
        </li>
        <li>
           <a href="/" class="flex items-center p-2  dark:text-white  dark:hover:bg-gray-700 group text-white border-l-2 border-white rounded-lg bg-gray-950 hover:bg-gray-700">
              <svg class="flex-shrink-0 w-5 h-5 text-gray-500 transition duration-75 dark:text-gray-400 group-hover:text-gray-900 dark:group-hover:text-white" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" fill="currentColor" viewBox="0 0 20 20">
                 <path d="m17.418 3.623-.018-.008a6.713 6.713 0 0 0-2.4-.569V2h1a1 1 0 1 0 0-2h-2a1 1 0 0 0-1 1v2H9.89A6.977 6.977 0 0 1 12 8v5h-2V8A5 5 0 1 0 0 8v6a1 1 0 0 0 1 1h8v4a1 1 0 0 0 1 1h2a1 1 0 0 0 1-1v-4h6a1 1 0 0 0 1-1V8a5 5 0 0 0-2.582-4.377ZM6 12H4a1 1 0 0 1 0-2h2a1 1 0 0 1 0 2Z"/>
              </svg>
              <span class="flex-1 ms-3 whitespace-nowrap">Inbox</span>
              <span class="inline-flex items-center justify-center w-3 h-3 p-3 ms-3 text-sm font-medium text-blue-800 bg-blue-100 rounded-full dark:bg-blue-900 dark:text-blue-300">3</span>
           </a>
        </li>
        <li>
           <a href="/" class="flex items-center p-2  dark:text-white  dark:hover:bg-gray-700 group text-white border-l-2 border-white rounded-lg bg-gray-950 hover:bg-gray-700">
              <svg class="flex-shrink-0 w-5 h-5 text-gray-500 transition duration-75 dark:text-gray-400 group-hover:text-gray-900 dark:group-hover:text-white" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" fill="currentColor" viewBox="0 0 20 18">
                 <path d="M14 2a3.963 3.963 0 0 0-1.4.267 6.439 6.439 0 0 1-1.331 6.638A4 4 0 1 0 14 2Zm1 9h-1.264A6.957 6.957 0 0 1 15 15v2a2.97 2.97 0 0 1-.184 1H19a1 1 0 0 0 1-1v-1a5.006 5.006 0 0 0-5-5ZM6.5 9a4.5 4.5 0 1 0 0-9 4.5 4.5 0 0 0 0 9ZM8 10H5a5.006 5.006 0 0 0-5 5v2a1 1 0 0 0 1 1h11a1 1 0 0 0 1-1v-2a5.006 5.006 0 0 0-5-5Z"/>
              </svg>
              <span class="flex-1 ms-3 whitespace-nowrap">Users</span>
           </a>
        </li>
        <li>
           <a href="/" class="flex items-center p-2  dark:text-white dark:hover:bg-gray-700 group text-white border-l-2 border-white rounded-lg bg-gray-950 hover:bg-gray-700">
              <svg class="flex-shrink-0 w-5 h-5 text-gray-500 transition duration-75 dark:text-gray-400 group-hover:text-gray-900 dark:group-hover:text-white" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" fill="currentColor" viewBox="0 0 18 20">
                 <path d="M17 5.923A1 1 0 0 0 16 5h-3V4a4 4 0 1 0-8 0v1H2a1 1 0 0 0-1 .923L.086 17.846A2 2 0 0 0 2.08 20h13.84a2 2 0 0 0 1.994-2.153L17 5.923ZM7 9a1 1 0 0 1-2 0V7h2v2Zm0-5a2 2 0 1 1 4 0v1H7V4Zm6 5a1 1 0 1 1-2 0V7h2v2Z"/>
              </svg>
              <span class="flex-1 ms-3 whitespace-nowrap">Products</span>
           </a>
        </li>
        <li>
           <a href="/" class="flex items-center p-2  dark:text-white  dark:hover:bg-gray-700 group text-white border-l-2 border-white rounded-lg bg-gray-950 hover:bg-gray-700">
              <svg class="flex-shrink-0 w-5 h-5 text-gray-500 transition duration-75 dark:text-gray-400 group-hover:text-gray-900 dark:group-hover:text-white" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 18 16">
                 <path stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M1 8h11m0 0L8 4m4 4-4 4m4-11h3a2 2 0 0 1 2 2v10a2 2 0 0 1-2 2h-3"/>
              </svg>
              <span class="flex-1 ms-3 whitespace-nowrap">Sign In</span>
           </a>
        </li>
        <li>
           <a href="/" class="flex items-center p-2  dark:text-white  dark:hover:bg-gray-700 group text-white border-l-2 border-white rounded-lg bg-gray-950 hover:bg-gray-700">
              <svg class="flex-shrink-0 w-5 h-5 text-gray-500 transition duration-75 dark:text-gray-400 group-hover:text-gray-900 dark:group-hover:text-white" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" fill="currentColor" viewBox="0 0 20 20">
                 <path d="M5 5V.13a2.96 2.96 0 0 0-1.293.749L.879 3.707A2.96 2.96 0 0 0 .13 5H5Z"/>
                 <path d="M6.737 11.061a2.961 2.961 0 0 1 .81-1.515l6.117-6.116A4.839 4.839 0 0 1 16 2.141V2a1.97 1.97 0 0 0-1.933-2H7v5a2 2 0 0 1-2 2H0v11a1.969 1.969 0 0 0 1.933 2h12.134A1.97 1.97 0 0 0 16 18v-3.093l-1.546 1.546c-.413.413-.94.695-1.513.81l-3.4.679a2.947 2.947 0 0 1-1.85-.227 2.96 2.96 0 0 1-1.635-3.257l.681-3.397Z"/>
                 <path d="M8.961 16a.93.93 0 0 0 .189-.019l3.4-.679a.961.961 0 0 0 .49-.263l6.118-6.117a2.884 2.884 0 0 0-4.079-4.078l-6.117 6.117a.96.96 0 0 0-.263.491l-.679 3.4A.961.961 0 0 0 8.961 16Zm7.477-9.8a.958.958 0 0 1 .68-.281.961.961 0 0 1 .682 1.644l-.315.315-1.36-1.36.313-.318Zm-5.911 5.911 4.236-4.236 1.359 1.359-4.236 4.237-1.7.339.341-1.699Z"/>
              </svg>
              <span class="flex-1 ms-3 whitespace-nowrap">Sign Up</span>
           </a>
        </li>
     </ul>
  </div>
</aside>




<!-- {/if} -->


<style>
    svg {
  -webkit-filter: invert(100%); /* safari 6.0 - 9.0 */
          filter: invert(100%);
          /* rotate: 180deg; */
}
    
.logo {
  background: #000000;
  color: #ffffff;
  position: relative;
  font-weight: 600;
  

 
}

.logo:after {
  /*content: "Yoink";*/
  content: attr(data-text);
  font-weight:600;
  display: block;
  position: absolute;
  top: 0px;
  height: 55%;
  overflow: hidden;
  background: #ffffff;
  color: #000000;

  
}
</style>