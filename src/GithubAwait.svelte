<script>
    async function getUsers(){
        let userData = await fetch('https://api.github.com/users');
        //let userData = await fetch('https://as-api-dev-dw.azurewebsites.net/api/Indikator/ekstern/hentAlleIndikatorer');
        let githubUsers = await userData.json();
        return githubUsers;
    }
</script>

<section>
    {#await getUsers()}
        loading
    {:then users}
    {#each users as user}
    <article class="user">
        <img src={user.avatar_url} alt={user.login}>
        <div class="user-info">
            <h3>User: {user.login}</h3>
            <a href={user.html_url} class="btn-primary" target="_blank">Github url</a>
        </div>
    </article>
    {/each}
    {:catch error}
    <p>Something went wrong</p>
    {/await}
</section>