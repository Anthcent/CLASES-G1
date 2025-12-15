# 🚀 Desafío Final: Inventario con Privacidad

**Misión Final:**

Crea una función llamada `manejarInventario` que reciba un `nombreProducto` (string) y una `cantidadInicial` (number). Esta función debe retornar un objeto con dos métodos:

1.  `agregarStock(cantidad)`: Un método que incremente el stock del producto por la `cantidad` especificada.
2.  `mostrarStock()`: Un método que imprima en consola el nombre del producto y su stock actual.

Asegúrate de que el stock y el nombre del producto sean privados (no accesibles directamente desde fuera de la función `manejarInventario`) utilizando `let` o `const` de forma apropiada para su scope. Prueba tu solución creando múltiples instancias de inventario y manipulándolas de forma independiente.

### Solución

```javascript
function manejarInventario(nombreProducto, cantidadInicial) {
    let stock = cantidadInicial;

    return {
        agregarStock: function(cantidad) {
            stock = stock + cantidad;
        },
        mostrarStock: function() {
            console.log(nombreProducto, stock);
        }
    };
}

const tiendaLibros = manejarInventario("Libro JavaScript", 50);
const tiendaTeclados = manejarInventario("Teclado Mecánico", 10);

tiendaLibros.mostrarStock();
tiendaLibros.agregarStock(20);
tiendaLibros.mostrarStock();

tiendaTeclados.mostrarStock();
```
