<script>
  let username = '';
  let password = '';
  let error = '';

  function handleSubmit(event) {
  event.preventDefault(); // Prevent the form from submitting and refreshing the page

  // Perform your authentication logic here
  if (username === localStorage.getItem('username') && password === localStorage.getItem('password')) {
    localStorage.setItem('isLoggedIn', 'true');
    error = '';

    // Redirect to the other application in another tab
    const otherAppURL = 'https://646dad3690cf0451df827f2a--quiet-tulumba-cfb481.netlify.app/';
    const params = {
      username: username,
      password: password
    };

    const otherAppWindow = window.open(otherAppURL, '_self'); // Open the other application in a new tab

    // Wait for the other application to load
    otherAppWindow.onload = () => {
      // Send message to the other application
      otherAppWindow.postMessage(params, otherAppURL);
    };
  } else {
    error = 'Invalid credentials';
    alert('Invalid credentials');
  }
}






</script>


<div class="login-form-container">
  <h1>Login</h1>
  <form on:submit="{handleSubmit}">
    <label>
      Username:
      <input type="text" bind:value="{username}" />
    </label>
    <label>
      Password:
      <input type="password" bind:value="{password}" />
    </label>
    <button type="submit">Login</button>
    {#if error}
      <p>{error}</p>
    {/if}
  </form>
</div>
<style>
 .login-form-container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  
}

.login-form-container h1 {
  text-align: center;
  margin-top: 0;
}

.login-form-container form {
  width: 50%;
}

.login-form-container label {
  display: block;
  margin-bottom: 10px;
}

.login-form-container input[type="text"],
.login-form-container input[type="password"] {
  width: 100%;
  padding: 5px;
  border: 1px solid #ccc;
}

.login-form-container button[type="submit"] {
  display: block;
  width: 100%;
  padding: 10px;
  margin-top: 10px;
  background-color: #4CAF50;
  color: white;
  border: none;
  cursor: pointer;
}

.login-form-container p {
  color: red;
  text-align: center;
}

</style>