# TITULO: GESTIÓN DE INVENTARIO
## Descripcion:
Como encargado del despacho de bodega quiero un sistema en consola que me permita registrar productos, visualizarlos y obtener resultados automaticos, para mantener un control preciso del stock manejado en bodega y conocer el valor de la inversion
### Como funciona
El sitema permite con un ciclo continuo de retroalimentacion basado en cuatro aspectos
###
* Interfaz de menu: Mediante un bucle while, el sistema presenta opciones numeradas. Utiliza logica condicional (if-elif-else) para dirigir al usuario a la funcionalidad deseada.
* Almacenamiento estructurado: utiliza una lista global que actua como base de datos volatil. Cada vez que se agrega un producto, se crea un diccionario con las claves nombre, precio, y cntidad asegurando que la informacion este relacionasda entre si.
* Procesamiento de datos: Para mostrar el sistema usa un bucle for que recorre la lista e imprime cada diccionario
   * para estadisticas, el sistema itera sobre la lista y realiza operaciones aritmeticas (precio x cantidad) para acumular totales.
   * validacion: el sistema esta blindado contra entradas invalidas; si el usuario elige una opcion inexistente o ingresa texto donde deberia haber numeros, informa el error y regresa al menu.
 
  ## Resultados
  funcion 

