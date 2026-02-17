<script>
    import Input from "./Input.svelte";
    import Dropdown from "./Dropdown.svelte";
    import Rangos from "./Rangos.svelte";

    let estado = {
        nombre: "Sergio",
        apellido: "García",
        sector: "Informática",
        salario: {
            min: 1000,
            max: 2000,
        },
    };

    let sectores = [
        "Backend",
        "Frontend",
        "Fullstack",
        "DevOps",
        "QA",
        "UX/UI",
    ];

    function envio(e) {
        e.preventDefault();
        alert(JSON.stringify(estado));
    }

    //FUNCION QUE FUNCIONABA ANTES
    // function actualizarSalario(e) {
    //     estado.salario = e.detail.min;
    //     estado.salario.max = e.detail.max;
    // }
    //FUNCION
    function actualizarSalario(datos) {
        // 'datos' es el objeto { min: 1000, max: 2000 } que envía el hijo
        estado.salario.min = datos.min;
        estado.salario.max = datos.max;
    }
</script>

<main>
    <form on:submit={envio}>
        <Input identifier="nombre" label="Nombre" bind:value={estado.nombre} />
        <Input
            identifier="apellido"
            label="Apellido"
            bind:value={estado.apellido}
        />
        <Dropdown
            identificador="sector"
            label="Sector"
            choices={sectores}
            bind:value={estado.sector}
        />
        <Rangos
            identificador="salario"
            label="Salario"
            min={estado.salario.min}
            max={estado.salario.max}
            onupdate={actualizarSalario}
        />
        <p>
            <input type="submit" value="Enviar" />
        </p>
    </form>
</main>
