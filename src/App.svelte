<script>
    let nombre = "";

    function handle(e) {
        const target = e.target;
        nombre = e.target.value;
        console.log(nombre);
    }
</script>


<input type="text" placeholder="Pon aqui tu nombre" on:keyup={handle}>

{#if nombre.length===0}
<p>El campo nombre no puede estar vacio</p>
{:else}
<p>un gusto conocerte {nombre}</p>
{/if}