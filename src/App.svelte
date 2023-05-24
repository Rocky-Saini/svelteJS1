<script>
	 import LoginForm from './LoginForm.svelte';
  import RegistrationForm from './RegistrationForm.svelte';

	import { onDestroy } from 'svelte';
  
	let isLoggedIn = localStorage.getItem('isLoggedIn') === 'true';
  
	function handleLogout() {
	  // Remove all credentials from localStorage and log the user out
	  localStorage.removeItem('isLoggedIn');
	  localStorage.removeItem('username');
	  localStorage.removeItem('password');
	  isLoggedIn = false;
	}
  
	onDestroy(() => {
	  // Clean up on component destruction
	  localStorage.removeItem('isLoggedIn');
	});
  </script>
  
  {#if isLoggedIn}
  <div class="container">

	  <h1>Are you sure Want to logout of this Application</h1>
	  <button on:click="{handleLogout}">Logout</button>
	  <!-- Your authenticated content goes here -->
  </div>
  {:else}
	<LoginForm />
	<RegistrationForm />
  {/if}
  <style>
	.container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  height: 100vh;
  text-align: center;
}

h1 {
  margin-top: 0px;
}

button {
  padding: 10px 20px;
  background-color: #4caf50;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

  </style>