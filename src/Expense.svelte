<script>
    import { getContext } from 'svelte';
    import { blur, slide, scale, fade, fly } from "svelte/transition";
   export let expense;
   let displayAmount = false;

   function toggleAmount(){
    displayAmount = !displayAmount;
   }

   const removeExpense = getContext('remove');
   const setModifiedExpense = getContext('modify');
</script>

<article class="single-expense">
<div class="expense-info">
    <h2>{expense.name} 
        <button class="amount-btn" on:click={toggleAmount}>
            <i class="fas fa-caret-down"></i>
        </button>
    </h2>

    {#if displayAmount}
    <h4 transition:slide>amount: ${expense.amount}</h4>
    {/if}
    
</div>
<div class="expense-buttons">
    <button class="expense-btn edit-btn" on:click={() => setModifiedExpense(expense.id)}>
        <i class="fas fa-pen"></i>
    </button>
    <button class="expense-btn delete-btn" on:click={() => removeExpense(expense.id)}>
        <i class="fas fa-trash"></i>
    </button>
</div>
</article>
