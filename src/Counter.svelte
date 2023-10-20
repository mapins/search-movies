<script>
	export let initialCounter = 0;//Lo que esta ocurriendo aqui es que coge el initialCounter de la propiedad de main, por lo que va a ser 5 y en el caso de que no le pasemos nada se pondra 0.
	let contador = initialCounter///ASIGNACION REACTIVA

	export let maxCounter=9

	
	function handleClick(){
		contador++;
	}

    //$: es una asignacion reactiva osea que svelte va a reconocer que ese valor va a ir cambiando cada vez que contador cambie.Esto es una manera 
    $: isEvenOrOdd = contador % 2 == 0 ? 'Is Even' : 'Is Odd'

	//Entonces en este caso lo que ocurre es que cuando cambia contador se llama a este efecto.Los efectos son totalmente depensientes, isEvenOrOdd es independiente de este
	/* $:{
		console.log('limit contador')
		if(contador>9){
			contador=9
		}
	} */

	//Si por ejemplo queremos que solo lo ejecute cuando ocurra esa conidicion ponemos la condicion antes.

	$:if(contador>maxCounter){
		console.log('limit contador')
		contador=maxCounter
	}


</script>




<!-- Esta parte de estilo solo se lo estamos dando unicamente a los span que hemos creado dentro del componente -->
<style>
	span{
        color: red;
    }
</style>

<main>
	<button on:click={handleClick}>Incrementar</button>
	<span>{contador}</span>
	<span>{isEvenOrOdd}</span>
   <!--  <span>{contador % 2 == 0 ? 'Is Even' : 'Is Odd'}</span> Y esto tambien va cambiando de valor porque se lo pasamos al renderizado -->
</main>