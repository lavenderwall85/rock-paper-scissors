<script>
    // Opciones de juego
    let opciones = ["Piedra", "Papel", "Tijera"];
    let eleccionJugador = ""; 
    let eleccionBot = ""; 
    let mensaje = ""; // 
    let victorias = 0; 
    let derrotas = 0; 
    let empates = 0; 

    // Función para jugar
    function jugar(opcion) {
        eleccionJugador = opcion; 
        eleccionBot = opciones[Math.floor(Math.random() * opciones.length)]; 

        // Comprobar quién gana
        if (eleccionJugador === eleccionBot) {
            mensaje = "Empate 😐";
            empates = empates + 1; 
        } else if (
            (eleccionJugador === "Piedra" && eleccionBot === "Tijera") ||
            (eleccionJugador === "Papel" && eleccionBot === "Piedra") ||
            (eleccionJugador === "Tijera" && eleccionBot === "Papel")
        ) {
            mensaje = "¡Ganaste! 🎉";
            victorias = victorias + 1; 
        } else {
            mensaje = "Perdiste 😢";
            derrotas = derrotas + 1; 
        }
    }

    // Función para reiniciar el juego
    function reiniciar() {
        eleccionJugador = "";
        eleccionBot = "";
        mensaje = "";
    }
</script>

<main>
    <h1>Piedra, Papel o Tijera</h1>

    {#if eleccionJugador === ""}
        <p>Elige una opción:</p>
        <button on:click={() => jugar("Piedra")}>Piedra</button>
        <button on:click={() => jugar("Papel")}>Papel</button>
        <button on:click={() => jugar("Tijera")}>Tijera</button>
    {:else}
        <p>Tu elección: {eleccionJugador}</p>
        <p>Elección del bot: {eleccionBot}</p>
        <h2>{mensaje}</h2>
        <button on:click={reiniciar}>Jugar otra vez</button>
    {/if}

    <div style="margin-top: 20px;">
        <h3>Puntuación</h3>
        <p>Victorias: {victorias}</p>
        <p>Derrotas: {derrotas}</p>
        <p>Empates: {empates}</p>
    </div>
</main>

<style>
    h1 {
        font-size: 24px;
        text-align: center;
    }
    p {
        font-size: 18px;
    }
    button {
        font-size: 16px;
        margin: 5px;
        padding: 10px;
        background-color: lightblue;
        border: none;
        border-radius: 5px;
        cursor: pointer;
    }
    button:hover {
        background-color: deepskyblue;
        color: white;
    }
    main {
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        min-height: 100vh; 
        text-align: center;
    }
</style>
