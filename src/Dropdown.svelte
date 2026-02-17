<script>
    export let identificador;
    export let label;
    export let choices;
    export let value;
</script>


<p>
    <label for={identificador}>{label}</label>
    <select id={identificador} bind:value>
        {#each choices as choice}
            <option value={choice}>{choice}</option>
        {/each}
    </select>
</p>
