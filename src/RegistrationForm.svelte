<script>
  let username = '';
  let password = '';
  let confirmPassword = '';
  let error = '';

  function handleSubmit() {
    // Perform your registration logic here
    if (password === confirmPassword) {
      localStorage.setItem('username', username);
      localStorage.setItem('password', password);
      error = '';
      navigateToLogin();
    } else {
      error = 'Passwords do not match';
      alert('Password do not match')
    }
  }

  function navigateToLogin() {
    // Redirect to the login page
    window.location.href = '/login';
  }
</script>


<div class="register-form-container">
  <h1>Register</h1>
  <form on:submit="{handleSubmit}">
    <label>
      Username:
      <input type="text" bind:value="{username}" />
    </label>
    <label>
      Password:
      <input type="password" bind:value="{password}" />
    </label>
    <label>
      Confirm Password:
      <input type="password" bind:value="{confirmPassword}" />
    </label>
    <button type="submit">Register</button>
    {#if error}
      <p>{error}</p>
    {/if}
  </form>
</div>

<style>
  .register-form-container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  
}

.register-form-container h1 {
  text-align: center;
  margin-top: 0;
}

.register-form-container form {
  width: 50%;
}

.register-form-container label {
  display: block;
  margin-bottom: 10px;
}

.register-form-container input[type="text"],
.register-form-container input[type="password"] {
  width: 100%;
  padding: 5px;
  border: 1px solid #ccc;
}

.register-form-container button[type="submit"] {
  display: block;
  width: 100%;
  padding: 10px;
  margin-top: 10px;
  background-color: #4CAF50;
  color: white;
  border: none;
  cursor: pointer;
}

.register-form-container p {
  color: red;
  text-align: center;
}

</style>



