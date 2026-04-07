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
  # Listado para almacenar los productos del inventario
inventario = []

def agregar_producto():
    """TASK 2: Permite al usuario ingresar datos y los guarda en un diccionario."""
    print("\n--- Agregar Nuevo Producto ---")
    nombre = input("Nombre del producto: ")
    
    # Validación básica para asegurar que el precio y cantidad sean números
    try:
        precio = float(input("Precio del producto: "))
        cantidad = int(input("Cantidad disponible: "))
        
        # Crear el diccionario y añadirlo a la lista
        producto = {
            "nombre": nombre,
            "precio": precio,
            "cantidad": cantidad
        }
        inventario.append(producto)
        print(f"¡{nombre} agregado con éxito!")
    except ValueError:
        print("Error: El precio y la cantidad deben ser valores numéricos.")

def mostrar_inventario():
    """TASK 3: Recorre la lista y muestra los productos en un formato legible."""
    print("\n--- Inventario Actual ---")
    if not inventario:
        print("El inventario está vacío.")
    else:
        for prod in inventario:
            # Formato claro de salida
            print(f"Producto: {prod['nombre']} | Precio: {prod['precio']} | Cantidad: {prod['cantidad']}")

def calcular_estadisticas():
    """TASK 4: Calcula el valor total y la cantidad total de artículos."""
    print("\n--- Estadísticas del Inventario ---")
    if not inventario:
        print("No hay datos suficientes para calcular estadísticas.")
        return

    valor_total = 0
    cantidad_total_articulos = 0

    for prod in inventario:
        valor_total += prod['precio'] * prod['cantidad']
        cantidad_total_articulos += prod['cantidad']

    print(f"Cantidad total de productos registrados: {len(inventario)}")
    print(f"Cantidad total de artículos en stock: {cantidad_total_articulos}")
    print(f"Valor total del inventario: ${valor_total:,.2f}")

def menu_principal():
    """TASK 1 & 2: Maneja el control de flujo y el menú interactivo."""
    while True:
        print("\n--- SISTEMA DE GESTIÓN DE INVENTARIO ---")
        print("1. Agregar producto")
        print("2. Mostrar inventario")
        print("3. Calcular estadísticas")
        print("4. Salir")
        
        opcion = input("Seleccione una opción (1-4): ")

        # Estructura condicional para procesar la opción elegida
        if opcion == "1":
            agregar_producto()
        elif opcion == "2":
            mostrar_inventario()
        elif opcion == "3":
            calcular_estadisticas()
        elif opcion == "4":
            print("Saliendo del sistema... ¡Hasta pronto!")
            break # Rompe el bucle while para finalizar
        else:
            # Validación de entrada inválida
            print("Opción no válida. Por favor, intente de nuevo.")

# Punto de entrada del programa
if __name__ == "__main__":
    menu_principal()


