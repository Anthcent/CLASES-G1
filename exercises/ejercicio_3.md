# 🧪 Ejercicio 3: Closures (Clausuras) y Encapsulación

Este ejercicio introduce uno de los conceptos más poderosos y a menudo malentendidos de JavaScript: los **Closures**.

### 🔍 Análisis del Ejemplo

Este ejemplo introduce el concepto de 'closures', una característica poderosa de JavaScript que depende directamente del scope léxico de las variables.
- **Persistencia de Scope**: Cuando una función interna (como `incrementar`) es retornada y sigue existiendo después de que su función externa (`crearContador`) ha terminado, la función interna 'cierra' sobre las variables de su scope padre.
- **Encapsulación**: Esto permite que las variables (como `contador`) persistan y mantengan su estado a través de múltiples llamadas a la función interna, creando un efecto de 'privacidad'. La variable `contador` no es directamente accesible desde fuera de la función retornada, solo a través de los métodos que expone el closure.
- **Independencia**: Cada llamada a `crearContador` genera un nuevo closure con su propio `contador` independiente.

### 🔑 Snippets / Conceptos Clave
*   `log` (console.log)
*   `func` (function)
*   `if` (condicional)
*   `map` / `filter` (métodos de array)
*   `state` / `effect` (conceptos de React, que usan closures internamente)
*   `import` (módulos)

### 💻 Código de Ejemplo

Ejecuta este código para ver cómo dos "contadores" creados por la misma fábrica mantienen estados totalmente separados.

```javascript
function crearContador() {
    // 'contador' es una variable local declarada con 'let'.
    // Está en el scope léxico de la función 'crearContador'.
    let contador = 0; 

    // Esta función interna 'incrementar' es retornada.
    // Forma un 'closure', lo que significa que "recuerda" y tiene acceso al 'contador'
    // del scope padre, incluso DESPUÉS de que 'crearContador' haya terminado de ejecutarse.
    return function incrementar() {
        contador = contador + 1; // Modificamos la variable 'contador' del scope externo.
        console.log("Contador actual:", contador);
        return contador;
    };
}

// Creamos dos instancias de contadores. Cada una tendrá su propio 'contador' privado.
const miContador1 = crearContador(); // 'miContador1' obtiene su propio 'contador' interno.
const miContador2 = crearContador(); // 'miContador2' obtiene SU PROPIO 'contador' interno, independiente del primero.

console.log("--- Interacciones con Contador 1 ---");
miContador1(); // La función 'incrementar' de miContador1 opera sobre SU 'contador'. Salida: Contador actual: 1
miContador1(); // Salida: Contador actual: 2
miContador1(); // Salida: Contador actual: 3

console.log("--- Interacciones con Contador 2 ---");
miContador2(); // La función 'incrementar' de miContador2 opera sobre SU 'contador'. Salida: Contador actual: 1 (inicia de nuevo para esta instancia)
miContador2(); // Salida: Contador actual: 2

// Si intentamos acceder a 'contador' directamente, dará error, porque es privada al closure.
// console.log(miContador1.contador); // Esto sería 'undefined' o un error si intentáramos acceder directamente.
```
