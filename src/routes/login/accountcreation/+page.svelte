<script>
    let username = '';
    let password = '';
    let retypePassword = '';

    let isPasswordValid = false;
    let isRetypePasswordValid = false;

    function validatePassword() {
        const passwordRegex = /^(?=.*\d)(?=.*[a-z])(?=.*[A-Z])(?=.*[!@#$%^&*]).{8,}$/;
        isPasswordValid = passwordRegex.test(password);
    }

    function validateRetypePassword() {
        isRetypePasswordValid = password === retypePassword;
    }

    function createAccount() {
        if (isPasswordValid && isRetypePasswordValid) {
            // Add your account creation logic here
            console.log('Creating account...');
        } else {
            console.log('Invalid password or retype password');
        }
    }
</script>

<main>
    <h1>Create an Account</h1>

    <form on:submit|preventDefault={createAccount}>
        <label for="username">Username:</label>
        <input type="text" id="username" bind:value={username} />

        <label for="password">Password:</label>
        <input type="password" id="password" bind:value={password} on:input={validatePassword} />
        {#if !isPasswordValid && password !== ''}
            {#if !/(?=.*\d)/.test(password)}
                <p>Password must contain a number.</p>
            {/if}
            {#if !/(?=.*[a-z])/.test(password)}
                <p>Password must contain a lowercase letter.</p>
            {/if}
            {#if !/(?=.*[A-Z])/.test(password)}
                <p>Password must contain an uppercase letter.</p>
            {/if}
            {#if !/(?=.*[!@#$%^&*])/.test(password)}
                <p>Password must contain a symbol.</p>
            {/if}
            {#if password.length < 8}
                <p>Password must be at least 8 characters long.</p>
            {/if}
        {/if}

        <label for="retype-password">Retype Password:</label>
        <input type="password" id="retype-password" bind:value={retypePassword} on:input={validateRetypePassword} />
        {#if !isRetypePasswordValid && password !== '' && retypePassword !== ''}
            <p>Passwords do not match.</p>
        {/if}

        <button type="submit">Create Account</button>
    </form>
</main>

<style>
    main {
        max-width: 400px;
        margin: 0 auto;
        padding: 2rem;
    }

    label {
        display: block;
        margin-bottom: 0.5rem;
    }

    input {
        width: 100%;
        padding: 0.5rem;
        margin-bottom: 1rem;
    }

    button {
        padding: 0.5rem 1rem;
        background-color: #007bff;
        color: #fff;
        border: none;
        cursor: pointer;
    }
</style>
