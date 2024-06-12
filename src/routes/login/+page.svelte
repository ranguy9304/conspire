<!-- // src/routes/login/+page.svelte -->

<script>
 import { signIn, signOut } from '@auth/sveltekit/client';
 import { page } from '$app/stores';

 let email = '';

 const handleEmailSignIn = () => {
     signIn('nodemailer', { email, callbackUrl: '/protected' });
 };

 const handleGoogleSignIn = () => {
     signIn('google', { callbackUrl: '/protected' });
 };

 const handleSignOut = () => {
     signOut();
 }
</script>

<div>

 {#if !$page.data.session}
<div class="h-[100vh] flex justify-center">

    <div class=" border-[1px] border-white h-[35vh]  w-[23vw] align-middle mt-48 flex flex-col justify-center rounded-3xl">

        <form on:submit={handleEmailSignIn} class="flex flex-col my-auto">
         <input label="Email" type="email" bind:value={email} class=" mt-8 w-[18vw] h-9 mx-auto bg-[rgb(28,28,28)] border-[1px] border-[#A8A8A8] rounded-sm mb-6" />
         <button class="mb-0">sign in with mail</button>
        </form>

        <div class="flex mb-5">
            <div class=" w-28 h-0 border-[1px] border-[#A8A8A8] m-auto"></div>
            or
            <div class=" w-28 h-0 border-[1px] border-[#A8A8A8] m-auto"></div>
        </div>
      
        <button on:click={handleGoogleSignIn} class=" mb-10 border-[1px] border-[#A8A8A8] rounded-sm w-40 mx-auto py-1 px-9">
         <!-- import an svg -->
            <img src="icons8-google.svg" alt="google logo" class="w-6 h-6 m-auto"/>
            
        </button>
      </div>

</div>

 {/if}

 {#if $page.data.session}

  <div>
   <button on:click={handleSignOut}>Sign out</button>
  </div>

 {/if}

</div>