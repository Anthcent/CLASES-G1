# 🧪 Ejercicio 2: Scope de Bloque (`var` vs `let` vs `const`)

Este ejercicio profundiza en la importancia del **scope de bloque** y por qué `let` y `const` son preferibles a `var` en el desarrollo moderno.

### 🔍 Análisis del Ejemplo

Este ejemplo es crucial para entender el 'scope de bloque'.
- **`var`**: No respeta los bloques (`{}` como los de un bucle `for` o una sentencia `if`). Tiene scope de función o global.
- **`let` y `const`**: Sí respetan los bloques. Las variables declaradas con ellos solo existen dentro del bloque donde fueron definidas.

**Por qué importa:**
Usar `let` y `const` evita errores comunes como que una variable de iteración (i) sea accesible y modificable fuera del bucle, lo que hace el código más predecible. `const` es ideal para valores que no deben cambiar dentro de una iteración específica.

### 🔑 Snippets / Conceptos Clave
*   `log` (console.log)
*   `func` (function)
*   `if` (condicional)
*   `map` / `filter` (métodos de array)
*   `state` / `effect` (conceptos de React)
*   `import` (módulos)

### 💻 Código de Ejemplo

Ejecuta el siguiente código para observar cómo `var` "escapa" del bucle, mientras que `let` y `const` se mantienen contenidos.

```javascript
console.log("--- Usando var (Problema de hoisting y scope de función) ---");
// 'var' tiene scope de función (o global si está fuera de cualquier función), no de bloque.
// Esto significa que la variable 'i' declarada con 'var' escapará del bucle 'for'.
for (var i = 0; i < 3; i++) {
    console.log("Dentro del bucle con var, i:", i);
}
console.log("Fuera del bucle con var, i:", i); // Sorprendentemente, 'i' es 3 aquí. Esto es porque 'var' no respeta el scope del bucle.

console.log("--- Usando let (Scope de Bloque Correcto) ---");
// 'let' tiene scope de bloque. Una nueva variable 'j' se crea para cada iteración del bucle.
// Esto previene que la variable "escape" del bloque donde fue declarada.
for (let j = 0; j < 3; j++) {
    console.log("Dentro del bucle con let, j:", j);
}
// console.log("Fuera del bucle con let, j:", j); // Descomentar esta línea causaría un ReferenceError: j is not defined.
                                                // La variable 'j' solo existe dentro del bloque del bucle.

console.log("--- Usando const (Uso para valores constantes dentro de un bloque) ---");
const numeros = [10, 20, 30]; // 'numeros' es un array constante, no podemos reasignar el array completo.

for (let k = 0; k < numeros.length; k++) {
    // 'k' se declara con 'let' porque su valor DEBE cambiar en cada iteración del bucle.
    const actual = numeros[k]; // 'actual' se declara con 'const' porque su valor NO cambia dentro de esta iteración.
                               // Es una constante para el alcance de este bloque de bucle.
    console.log("Número en la posición", k, "es:", actual);
    // Intentar reasignar 'actual' aquí daría un error: actual = 5; // TypeError: Assignment to constant variable.
}
// console.log("Fuera del bucle con let (k):", k); // Error, 'k' está fuera de scope.
// console.log("Fuera del bucle con const (actual):", actual); // Error, 'actual' está fuera de scope.
```
