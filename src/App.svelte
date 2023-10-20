<script>
	import Counter from "./Counter.svelte";
	import Input from "./Input.svelte";
	const commonProps ={ maxCounter: 5 }
</script>



<!-- Lo que le estamos pasando son las propiedades-->
<Counter initialCounter={2} {...commonProps}/> <!-- Lo que hago con los tres puntos es que le propago las propiedades que le hemos puesto arriba. -->
<Counter initialCounter={10} {...commonProps}/>
<Counter {...commonProps}/>

<Input/>


<!-- En este caso nos ha creado un componente con valor predeterminado 0 ya que se lo hemos dado en Counter -->


<span>Hola</span>

<!-- Y en este caso le estamos dando estilo al span que hemos creado dentro del componente -->
<style>
	span{
		color: blue;
	}
</style>