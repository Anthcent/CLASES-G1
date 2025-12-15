# 🧪 Ejercicio 1: Variables y Scope (`let` vs `const`)

Este ejercicio se centra en comprender cómo funcionan las variables en JavaScript, específicamente la diferencia entre `let` y `const`, y cómo afecta el **scope** (alcance) a su visibilidad.

### 🔍 Análisis del Ejemplo

Este ejemplo muestra la diferencia fundamental entre `let` y `const`. 
- **`let`**: Permite la reasignación. Tiene un scope de bloque.
- **`const`**: No permite la reasignación (es constante). Tiene un scope de bloque.

**Reglas de Scope:**
Las variables declaradas globalmente o en scopes superiores son accesibles desde scopes internos (como dentro de funciones), pero las variables declaradas dentro de una función **no** son accesibles desde fuera de esa función. Esto es clave para evitar colisiones de nombres y controlar el flujo de datos.

### 🔑 Snippets / Conceptos Clave
Lista de estructuras y palabras clave utilizadas frecuentemente en este tipo de ejercicios:

*   `log` (console.log)
*   `func` (function)
*   `if` (condicional)
*   `map` / `filter` (métodos de array)
*   `state` / `effect` (conceptos de React, relacionados con el scope)
*   `import` (módulos)

### 💻 Código de Ejemplo

Copia y ejecuta este código para ver el comportamiento en acción. Intenta descomentar las líneas que causan errores para ver qué sucede.

```javascript
// Declaración de variables en el scope global
let nombre = "Juan"; // 'let' permite reasignar el valor. Su scope es de bloque.
const PI = 3.14159; // 'const' declara una constante, NO puede ser reasignada. Su scope es de bloque.

console.log("Nombre global:", nombre); // Acceso directo en el scope global
console.log("PI global:", PI); // Acceso directo en el scope global

// --- PRUEBA DE REASIGNACIÓN ---
// Intentar reasignar 'const' resultará en un error en tiempo de ejecución (TypeError).
// PI = 3.0; // Descomentar esta línea causaría un error: Assignment to constant variable.

nombre = "Pedro"; // 'let' puede ser reasignado sin problemas
console.log("Nombre reasignado:", nombre);

// --- PRUEBA DE SCOPE (ALCANCE) ---
function saludar() {
    // Las funciones crean un nuevo scope. Las variables del scope padre son accesibles (scope chain).
    console.log("Dentro de la función - Nombre:", nombre); // 'nombre' es accesible aquí desde el scope global.
    console.log("Dentro de la función - PI:", PI); // 'PI' también es accesible desde el scope global.

    let mensaje = "Hola"; // 'mensaje' tiene scope de función y solo existe dentro de 'saludar'.
    // console.log(otraVariable); // Esto causaría un ReferenceError si 'otraVariable' no está declarada aquí o en un scope superior.
}

saludar();

// --- INTENTO DE ACCESO A VARIABLES LOCALES ---
// console.log(mensaje); // Descomentar esta línea causaría un ReferenceError: mensaje is not defined, porque 'mensaje' está fuera de su scope.
```
