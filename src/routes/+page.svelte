<script>
    import { onMount } from 'svelte';

    function checkLoggedIn() {
        return false
    }
    onMount(() => {
        const isLoggedIn = checkLoggedIn();

        if (isLoggedIn) {
            window.location.href = '/dashboard';
        } else {
            window.location.href = '/login';
        }
    });
</script>
