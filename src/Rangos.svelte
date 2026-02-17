<script>
    // 1. Recibimos props y la función 'onupdate'
    let { label, identificador, min, max, onupdate } = $props();

    function cambiarMin(e) {
        const nuevoMin = parseInt(e.target.value);
        // 2. Ejecutamos la función que nos pasó el padre
        if (onupdate) {
            onupdate({ min: nuevoMin, max });
        }
    }

    function cambiarMax(e) {
        const nuevoMax = parseInt(e.target.value);
        if (onupdate) {
            onupdate({ min, max: nuevoMax });
        }
    }
</script>

<div class="rango-container">
    <p>
        <label for={`${identificador}_min`}>{label} mínimo</label>
        <input
            id={`${identificador}_min`}
            type="range"
            min="0"
            max="50000"
            value={min}
            oninput={cambiarMin}
        />
        <span>{min}</span>
    </p>

    <p>
        <label for={`${identificador}_max`}>{label} máximo</label>
        <input
            id={`${identificador}_max`}
            type="range"
            min="0"
            max="50000"
            value={max}
            oninput={cambiarMax}
        />
        <span>{max}</span>
    </p>
</div>
