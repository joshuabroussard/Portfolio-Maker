<script>
    let email = '';
    let password = '';

    function handleSubmit() {
        // Handle form submission here
        console.log('Email:', email);
        console.log('Password:', password);
    }
</script>

<main>
    <h1>Login</h1>
    <form on:submit={handleSubmit}>
        <label for="email">Email:</label>
        <input type="email" id="email" bind:value={email} required>

        <label for="password">Password:</label>
        <input type="password" id="password" bind:value={password} required>

        <button type="submit">Login</button>
    </form>
    
    <div>
        <button ><a href="/login/accountcreation">Create an Account</a></button>
        <button on:click={() => {}}>Forgot password</button>
    </div>
</main>
