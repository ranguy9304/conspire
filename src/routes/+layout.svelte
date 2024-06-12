

<script>
    import "../app.css";
    import Navbar from "../components/Navbar.svelte";
  // import Sidebar from "../components/Sidebar.svelte";
</script>
  
<!-- use tailwind -->
<div class="mainContainer overscroll-contain	">
    <Navbar/>
    <!-- <Sidebar/> -->
     <!-- like tracker graph ? like stock market, you triple click on likes it opens the graph -->
      <!-- for every theory there will be a sort description like heading 3 or 4 words and there will be a longer description -->
    <slot/>
</div>


<style>
    .mainContainer {
      background-color:black ;
      color:white;
      height:100%;
    }
</style>