<script>
    import SectionTitle from './Title.svelte'
    import Expense from './Expense.svelte'
    export let expenses = [];
</script>

<style>
    h2{
        text-transform: capitalize;
    }
</style>

<section>
    <SectionTitle title="expense list" />
    <ul>
        {#each expenses as expense, index (expense.id)}
            <Expense expense={expense} />
            {:else}
            <h2>No expenses added to the list</h2>
        {/each}
    </ul>
    
</section>