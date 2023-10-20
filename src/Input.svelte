<!-- LA PARTE DE SCRIPT ES LA PARTE LOGICA -->
<script>

    let value=''
    let response = []
    let loading=false

    const handleInput =(event) => 
    value = event.target.value
    /*  target es el elemento del DOM que esta en ese momento recibiendo ese momento y el value es el que estamos rellenando en el input*/

    $: if(value.length > 2){
        loading=true
        fetch(`https://www.omdbapi.com/?s=${value}&apikey=422350ff`)
        .then(res=>res.json())
        .then(apiResponse=>{
            response=apiResponse.Search || [] //Ponemmos este array vacio cuando no encuentre ninguna pelicula por ejemplo con aveng pues que nos de uno vaio
            loading=false
        })
    }

</script>

<!-- EN ESTA PARTE SE DENOMINA COMO EL MARCADO DEL COMPONENTE -->
<!-- Este código puede incluir HTML, lógica de control de flujo condicional, iteración y manipulación del DOM sin necesidad de estar envuelto en funciones JavaScript. -->
<input 
placeholder="Search movies" 
value={value} 
on:input={handleInput}
/>

//Esto es un renderizdo condicional, como sabemos que los valores que van a ir cambiando creamos esto.

{#if loading}
    <strong>Loading...</strong>
 {:else}
    {#if response.length>0}
        <strong>enemos ${response.length} peliculas</strong>
    {:else}
        <strong>No hay resultados</strong>
{/if}

{/if}



