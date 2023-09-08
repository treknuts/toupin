<script>
  import { onMount } from "svelte";
  let isLoggedIn;
  onMount(() => {
    if (window.netlifyIdentity) {
      window.netlifyIdentity.on("init", (user) => {
        if (!user) {
          isLoggedIn = false;
          window.netlifyIdentity.on("login", () => {
            document.location.href = "/admin/";
          });
        } else {
          isLoggedIn = true;
        }
      });
    }
  });
</script>

{#if isLoggedIn}
  <a href="https://toupin.netlify.app/admin">Backend</a>
{:else}
  <a href="https://toupin.netlify.app/admin">Login</a>
{/if}
