# 🎓 CLASES-G1

Bienvenido al repositorio **CLASES-G1** — un espacio para organizar materiales, ejercicios y recursos de la asignatura.

---

## 📌 Descripción

Material de clase, ejercicios y ejemplos prácticos organizados por tema.

---

## 4. Funciones tradicionales (JavaScript)

Las funciones tradicionales (declaradas con `function`) siguen siendo útiles en muchas situaciones. A continuación tienes una explicación breve y un ejemplo profesional, formateado para que se vea bien en GitHub.

### Ejemplo: `calcularTotalPedido`

```js
/**
 * Calcula el precio total de un pedido, aplicando descuento e impuesto.
 * @param {Array<Object>} productos - Array de objetos: { id, nombre, precio, cantidad }
 * @param {number} [descuentoPorcentaje=0] - Porcentaje de descuento (ej. 10)
 * @param {number} [impuestoPorcentaje=0] - Porcentaje de impuesto (ej. 16)
 * @returns {number} Total final (0 si no hay productos válidos)
 */
function calcularTotalPedido(productos, descuentoPorcentaje = 0, impuestoPorcentaje = 0) {
  if (!Array.isArray(productos) || productos.length === 0) return 0;

  let subtotal = 0;

  for (const producto of productos) {
    if (producto && typeof producto.precio === 'number' && typeof producto.cantidad === 'number') {
      subtotal += producto.precio * producto.cantidad;
    } else {
      console.warn('Producto inválido encontrado y omitido:', producto);
    }
  }

  const descuento = Math.max(0, Number(descuentoPorcentaje) || 0);
  const montoDescuento = subtotal * (descuento / 100);
  const subtotalConDescuento = subtotal - montoDescuento;

  const impuesto = Math.max(0, Number(impuestoPorcentaje) || 0);
  const montoImpuesto = subtotalConDescuento * (impuesto / 100);

  return subtotalConDescuento + montoImpuesto;
}

// Ejemplo rápido
const listaDeProductos1 = [
  { id: 'p001', nombre: 'Laptop Gamer', precio: 1200, cantidad: 1 },
  { id: 'p002', nombre: 'Teclado Mecánico', precio: 150, cantidad: 2 },
  { id: 'p003', nombre: 'Mouse RGB', precio: 50, cantidad: 1 }
];

console.log(calcularTotalPedido(listaDeProductos1)); // 1550.00
console.log(calcularTotalPedido(listaDeProductos1, 10, 16)); // 1618.20
```

---

## 5. Errores comunes

- Olvidar los paréntesis `()` al definir o al llamar.
- Olvidar `return` cuando se espera un valor (la función devuelve `undefined`).
- Confundir el alcance (`scope`) de variables; `let`/`const` son locales a la función.
- `this` puede cambiar según cómo se invoque la función; las arrow functions mantienen `this` léxico.
- Llamar con tipos o número de argumentos incorrectos puede producir `NaN`.

---

Si quieres un estilo visual concreto (por ejemplo, más emojis, un índice al inicio, o secciones plegables), dime y lo adapto.
# 🎓 CLASES-G1

Bienvenido al repositorio **CLASES-G1** — un espacio para organizar materiales, ejercicios y recursos de la asignatura.

---

## 📌 Descripción

Resumen corto y útil del proyecto. Coloca aquí el propósito del repositorio, por ejemplo:

- Material de clases y ejercicios.
- Recursos y apuntes por temática.
- Plantillas y ejemplos para prácticas.

## 🚦 Estado

- Estado: **En desarrollo**
- Última actualización: 2025-12-14

## 📁 Estructura del repositorio

Una vista rápida de los archivos y carpetas principales:

- `docs/` — Documentación complementaria (opcional)
- `src/` — Código fuente o ejemplos (si aplica)
- `exercises/` — Ejercicios y soluciones
- `assets/` — Imágenes y recursos estáticos
- `readme.md` — Este archivo

> Si alguna carpeta falta, añádela según tus necesidades.

## 🛠️ Instalación

Pasos rápidos para preparar el entorno (ejemplo genérico):

```bash
# Clonar el repositorio
git clone https://github.com/tu-usuario/CLASES-G1.git
cd CLASES-G1

# Crear entorno (ejemplo Python)
python -m venv .venv
source .venv/bin/activate  # Windows: .\.venv\Scripts\activate
pip install -r requirements.txt
```

Adapta los comandos según el lenguaje y herramientas que uses.

---

## 4. Funciones tradicionales (JavaScript)

Las funciones tradicionales (declaradas con la palabra clave `function`) son una forma clásica de encapsular lógica en JavaScript. A continuación se muestra una explicación clara y un ejemplo profesional para un caso real (cálculo de totales en un e‑commerce).

### ¿Qué veremos?

- Validación de parámetros
- Cálculo de subtotal, descuento e impuestos
- Ejemplos de uso

### Ejemplo: `calcularTotalPedido`

```js
/**
 * Calcula el precio total de un pedido, aplicando descuento e impuesto.
 * @param {Array<Object>} productos - Array de objetos con { id, nombre, precio, cantidad }
 * @param {number} [descuentoPorcentaje=0] - Porcentaje de descuento (ej. 10)
 * @param {number} [impuestoPorcentaje=0] - Porcentaje de impuesto (ej. 16)
 * @returns {number} Total final (0 si no hay productos válidos)
 */
function calcularTotalPedido(productos, descuentoPorcentaje = 0, impuestoPorcentaje = 0) {
  if (!Array.isArray(productos) || productos.length === 0) return 0;

  let subtotal = 0;

  for (const producto of productos) {
    if (producto && typeof producto.precio === 'number' && typeof producto.cantidad === 'number') {
      subtotal += producto.precio * producto.cantidad;
    } else {
      console.warn('Producto inválido encontrado y omitido:', producto);
    }
  }

  const descuento = Math.max(0, Number(descuentoPorcentaje) || 0);
  const montoDescuento = subtotal * (descuento / 100);
  const subtotalConDescuento = subtotal - montoDescuento;

  const impuesto = Math.max(0, Number(impuestoPorcentaje) || 0);
  const montoImpuesto = subtotalConDescuento * (impuesto / 100);

  return subtotalConDescuento + montoImpuesto;
}

// Ejemplos de uso
const listaDeProductos1 = [
  { id: 'p001', nombre: 'Laptop Gamer', precio: 1200, cantidad: 1 },
  { id: 'p002', nombre: 'Teclado Mecánico', precio: 150, cantidad: 2 },
  { id: 'p003', nombre: 'Mouse RGB', precio: 50, cantidad: 1 }
];

console.log(calcularTotalPedido(listaDeProductos1)); // 1550.00
console.log(calcularTotalPedido(listaDeProductos1, 10, 16)); // 1618.20
```

---

## 5. Errores comunes al trabajar con funciones tradicionales

1. Olvidar los paréntesis `()` al definir o llamar

   - Error: `function miFuncion { ... }` o `console.log(miFuncion);` (sin paréntesis)
   - Solución: usar `function miFuncion() { ... }` y `miFuncion()` para invocar.

2. No usar `return` cuando se espera un valor

   ```js
   function sumar(a, b) {
     const suma = a + b;
     // falta `return suma;`
   }
   ```

   - Resultado: la llamada devuelve `undefined`.

3. Alcance (scope) de variables

   - Las variables declaradas con `let`/`const` dentro de una función son locales.
   - Para usar un valor fuera, devuelve con `return`.

4. `this` dinámico en funciones tradicionales

   - En callbacks y temporizadores el valor de `this` puede perder el contexto.
   - Alternativas: `const self = this;` o usar funciones flecha para heredar `this` léxico.

5. Tipos y número de argumentos

   - Validar parámetros o usar TypeScript para evitar `NaN` y errores lógicos.

---

Si quieres, puedo:

- Añadir más ejemplos (tests unitarios, casos límite).
- Convertir este ejemplo a TypeScript.
- Extraer utilidades (validadores) y añadir un `README` por carpeta `src/`.
4. Funciones Tradicionales
JS / React / Node
¡Claro que sí! Como tu Mentor de Programación Senior, te guiaré a través de las "Funciones Tradicionales" en JavaScript, un pilar fundamental en cualquier aplicación que construyas con JS, React o Node. Prepárate para una explicación profunda y clara.
# 🎓 CLASES-G1

Bienvenido al repositorio **CLASES-G1** — un espacio para organizar materiales, ejercicios y recursos de la asignatura.

---

## 📌 Descripción

Resumen corto y útil del proyecto. Coloca aquí el propósito del repositorio, por ejemplo:

- Material de clases y ejercicios.
- Recursos y apuntes por temática.
- Plantillas y ejemplos para prácticas.

## 🚦 Estado

- Estado: **En desarrollo**
- Última actualización: 2025-12-14

## 📁 Estructura del repositorio

Una vista rápida de los archivos y carpetas principales:

- `docs/` — Documentación complementaria (opcional)
- `src/` — Código fuente o ejemplos (si aplica)
- `exercises/` — Ejercicios y soluciones
- `assets/` — Imágenes y recursos estáticos
- `readme.md` — Este archivo

> Si alguna carpeta falta, añádela según tus necesidades.

## ⚙️ Requisitos

Indica aquí las dependencias o requisitos del proyecto (lenguajes, versiones, librerías). Ejemplo genérico:

- Python 3.8+ o Node.js 14+
- Paquetes: lista en `requirements.txt` o `package.json`

Si no hay requisitos, reemplaza esta sección por "Ninguno".

## 🛠️ Instalación

Pasos rápidos para preparar el entorno (ejemplo genérico):

```bash
# Clonar el repositorio
git clone https://github.com/tu-usuario/CLASES-G1.git
cd CLASES-G1

# Crear entorno (ejemplo Python)
python -m venv .venv
source .venv/bin/activate  # Windows: .\.venv\Scripts\activate
pip install -r requirements.txt
```

Adapta los comandos según el lenguaje y herramientas que uses.

## ▶️ Uso

Explica cómo ejecutar ejemplos o abrir materiales. Ejemplos:

```bash
# Ejecutar un script de ejemplo (Python)
python src/ejemplo.py

# Abrir un cuaderno Jupyter
jupyter notebook
```

## 🤝 Contribuir

1. Haz un fork del repositorio.
2. Crea una rama: `git checkout -b feature/nombre`
3. Añade cambios y pruebas.
4. Envía un Pull Request describiendo tus cambios.

Por favor, mantén las contribuciones ordenadas y con commits claros.

## 📝 Buenas prácticas para commits

- Mensajes claros y en español/inglés según convención.
- Un cambio lógico por commit.

## 📬 Contacto

Si tienes preguntas o sugerencias, abre un *issue* o contacta al autor.

---

¿Quieres que incluya secciones específicas (diapositivas, calendario, rúbrica)? Indícame y lo añado.


---


4. Funciones Tradicionales

Las funciones son el corazón de la modularidad y la reutilización del código en JavaScript. Las funciones tradicionales, también conocidas como "function declarations" o "function expressions", han sido la forma estándar de definir bloques de código ejecutable desde los inicios del lenguaje.


---


#### 1. ¿Qué es?


Una función tradicional en JavaScript es un bloque de código reusable diseñado para realizar una tarea específica. Piensa en ella como una "mini-programa" o una "máquina" a la que le puedes dar unas entradas (parámetros) y ella te devuelve un resultado (valor de retorno), o simplemente realiza una acción.


Propósitos clave:

* Modularidad: Permiten dividir un programa complejo en unidades más pequeñas y manejables.
* Reusabilidad (Principio DRY - Don't Repeat Yourself): Evitan la duplicación de código. Si necesitas realizar la misma tarea en diferentes partes de tu aplicación, la defines una vez en una función y la llamas cuantas veces sea necesario.
* Abstracción: Ocultan la complejidad interna de una operación, permitiéndonos usarla sin preocuparnos por cómo funciona por dentro.
* Organización: Mejoran la legibilidad y estructura del código, haciendo que sea más fácil de entender y mantener.

En JavaScript, las funciones son "ciudadanos de primera clase". Esto significa que pueden ser tratadas como cualquier otro valor: asignadas a variables, pasadas como argumentos a otras funciones, o devueltas como resultado de otras funciones.


---


#### 2. Anatomía de la Sintaxis


La sintaxis de una función tradicional es bastante directa y se compone de varios elementos clave:


// Declaración de una función tradicional
function nombreDeLaFuncion(parametro1, parametro2) {
  // Cuerpo de la función: aquí va el código que la función ejecutará.
  let resultado = parametro1 + parametro2;
  return resultado; // Opcional, pero común para devolver un valor.
}

Desglosemos cada parte:


* `function` (Palabra Clave):
* ¿Qué es?: Es la palabra clave que *declara* que lo que sigue es una definición de función. Es indispensable para crear una función tradicional.
* ¿Por qué?: Le indica al motor de JavaScript que debe interpretar el bloque de código subsiguiente como una función ejecutable.

* `nombreDeLaFuncion` (Nombre de la Función):
* ¿Qué es?: Es un identificador único que le asignas a tu función. Sigue las mismas reglas de nomenclatura que las variables (generalmente `camelCase` para funciones).
* ¿Por qué?: Permite que puedas *llamar* (ejecutar) la función por su nombre en cualquier otra parte de tu código. Un nombre descriptivo es crucial para la legibilidad.

* `()` (Paréntesis):
* ¿Qué son?: Son obligatorios y envuelven la lista de *parámetros* que la función espera recibir.
* ¿Por qué?: Aunque una función no reciba ningún parámetro, los paréntesis deben estar presentes (e.g., `function saludar() { ... }`). Si la función espera entradas, aquí se declaran los nombres de las variables que representarán esas entradas dentro de la función.

* `parametro1, parametro2` (Parámetros - Opcionales):
* ¿Qué son?: Son variables locales que se declaran dentro de los paréntesis de la función. Actúan como "marcadores de posición" para los valores que se pasarán a la función cuando esta sea llamada.
* ¿Por qué?: Permiten que la función sea flexible y opere con diferentes datos cada vez que se ejecuta, sin tener que reescribir la lógica interna. Cuando llamas a la función, los valores que le pasas se conocen como *argumentos*.

* `{}` (Llaves - Cuerpo de la Función):
* ¿Qué son?: Delimitan el bloque de código que se ejecutará cada vez que se llame a la función.
* ¿Por qué?: Todo el código que define la tarea de la función debe ir dentro de estas llaves.

* `return` (Palabra Clave - Opcional):
* ¿Qué es?: Es una palabra clave que, si se utiliza, especifica el valor que la función debe *devolver* al código que la llamó.
* ¿Por qué?:
* Devuelve un valor: Permite que la función entregue un resultado para que pueda ser utilizado por otras partes del programa.
* Finaliza la ejecución: Una vez que se encuentra una declaración `return`, la función termina su ejecución inmediatamente, y cualquier código que esté después del `return` dentro de la misma función no se ejecutará. Si una función no tiene una declaración `return` explícita, o si el `return` se ejecuta sin un valor, la función devuelve `undefined` por defecto.

---


#### 3. Ejemplo Profesional


Imaginemos que estamos desarrollando una API en Node.js para un sistema de e-commerce, y necesitamos una función para calcular el precio total de un pedido, aplicando descuentos e impuestos.


/**
 * @function calcularTotalPedido
 * @description Calcula el precio total de un pedido de e-commerce, aplicando descuentos e impuestos.
 *              Esta función es un ejemplo de cómo encapsular lógica de negocio compleja
 *              para reutilizarla en diferentes puntos de la aplicación (ej. carrito, checkout).
 * @param {Array<Object>} productos - Un array de objetos, donde cada objeto representa un producto.
 *                                     Cada producto debe tener propiedades como `id`, `nombre`, `precio` y `cantidad`.
 * @param {number} [descuentoPorcentaje=0] - El porcentaje de descuento a aplicar al subtotal (ej. 10 para un 10%).
 *                                          Por defecto es 0 si no se especifica.
 * @param {number} [impuestoPorcentaje=0] - El porcentaje de impuesto a añadir al subtotal después del descuento (ej. 16 para un 16%).
 *                                          Por defecto es 0 si no se especifica.
 * @returns {number} El precio total final del pedido, o 0 si no hay productos.
 */
function calcularTotalPedido(productos, descuentoPorcentaje = 0, impuestoPorcentaje = 0) {
  // 1. Validaciones iniciales: Es una buena práctica validar las entradas para evitar errores inesperados.
  //    Verifica si 'productos' no es un array o si está vacío.
  if (!Array.isArray(productos) || productos.length === 0) {
    console.warn("Advertencia: No se han proporcionado productos válidos para el cálculo del pedido.");
    // Si no hay productos, el total es 0. El 'return' finaliza la ejecución de la función aquí.
    return 0;
  }
  // 2. Inicialización del subtotal:
  //    Esta variable acumulará el costo total de todos los productos antes de descuentos e impuestos.
  let subtotal = 0;
  // 3. Cálculo del subtotal base:
  //    Itera sobre cada producto en el array 'productos'. El bucle 'for...of' es moderno y legible
  //    para recorrer colecciones directamente.
  for (const producto of productos) {
    // Asegura que el producto y sus propiedades existan y sean números válidos para evitar NaN.
    if (producto && typeof producto.precio === 'number' && typeof producto.cantidad === 'number') {
      // Suma el precio unitario multiplicado por la cantidad al subtotal.
      subtotal += producto.precio * producto.cantidad;
    } else {
      // Si un producto no es válido, se podría loggear un error o ignorarlo.
      console.warn(`Producto inválido encontrado y omitido:`, producto);
    }
  }
  // 4. Aplicación del descuento:
  //    Se convierte el porcentaje de descuento a un factor (ej. 10% -> 0.10) y se calcula el monto a restar.
  //    Se asegura que el descuentoPorcentaje sea un número válido y no negativo.
  const descuentoAplicable = Math.max(0, typeof descuentoPorcentaje === 'number' ? descuentoPorcentaje : 0);
  const montoDescuento = subtotal * (descuentoAplicable / 100);
  const subtotalConDescuento = subtotal - montoDescuento;
  // 5. Aplicación del impuesto:
  //    Se calcula el impuesto sobre el subtotal *después* de aplicar el descuento.
  //    Se asegura que el impuestoPorcentaje sea un número válido y no negativo.
  const impuestoAplicable = Math.max(0, typeof impuestoPorcentaje === 'number' ? impuestoPorcentaje : 0);
  const montoImpuesto = subtotalConDescuento * (impuestoAplicable / 100);
  // 6. Cálculo del total final:
  const totalFinal = subtotalConDescuento + montoImpuesto;
  // 7. Retorno del valor calculado:
  //    La palabra clave 'return' envía el 'totalFinal' de vuelta al punto donde la función fue llamada.
  //    También detiene la ejecución de la función.
  return totalFinal;
}
// --- EJEMPLOS DE USO PROFESIONAL ---
// Datos de productos para un pedido
const listaDeProductos1 = [
  { id: 'p001', nombre: 'Laptop Gamer', precio: 1200, cantidad: 1 },
  { id: 'p002', nombre: 'Teclado Mecánico', precio: 150, cantidad: 2 },
  { id: 'p003', nombre: 'Mouse RGB', precio: 50, cantidad: 1 }
];
const listaDeProductos2 = [
  { id: 'p004', nombre: 'Monitor UltraWide', precio: 700, cantidad: 1 }
];
const listaDeProductosVacia = [];
const listaConProductoInvalido = [
  { id: 'p005', nombre: 'Webcam HD', precio: 75, cantidad: 1 },
  { id: 'p006', nombre: 'Micrófono USB', precio: 'cien', cantidad: 1 } // Precio inválido
];
// Caso 1: Calcular el total de un pedido sin descuentos ni impuestos.
// Se llama a la función y se le pasan los argumentos requeridos.
const totalPedido1 = calcularTotalPedido(listaDeProductos1);
console.log(`\nTotal Pedido 1 (sin descuento/impuesto): $${totalPedido1.toFixed(2)}`); // Esperado: 1200 + (150*2) + 50 = 1550.00
// Caso 2: Calcular el total con un descuento del 10% y un impuesto del 16%.
const totalPedido2 = calcularTotalPedido(listaDeProductos1, 10, 16);
console.log(`Total Pedido 2 (10% desc, 16% imp): $${totalPedido2.toFixed(2)}`);
// Subtotal: 1550
// Descuento (10%): 1550 * 0.10 = 155
// Subtotal con descuento: 1550 - 155 = 1395
// Impuesto (16%): 1395 * 0.16 = 223.2
// Total Final: 1395 + 223.2 = 1618.20
// Caso 3: Calcular el total para un solo producto con impuestos.
const totalPedido3 = calcularTotalPedido(listaDeProductos2, 0, 8);
console.log(`Total Pedido 3 (sin desc, 8% imp): $${totalPedido3.toFixed(2)}`);
// Subtotal: 700
// Descuento: 0
// Impuesto (8%): 700 * 0.08 = 56
// Total Final: 700 + 56 = 756.00
// Caso 4: Intentar calcular un pedido con una lista de productos vacía.
const totalPedido4 = calcularTotalPedido(listaDeProductosVacia, 5, 10);
console.log(`Total Pedido 4 (lista vacía): $${totalPedido4.toFixed(2)}`); // Esperado: 0.00
// Caso 5: Pedido con un producto inválido (se omite y se calcula el resto).
const totalPedido5 = calcularTotalPedido(listaConProductoInvalido, 0, 0);
console.log(`Total Pedido 5 (con producto inválido): $${totalPedido5.toFixed(2)}`);
// Esperado: Sólo se considera la webcam: 75.00

---


#### 4. Errores Comunes


Incluso con la sintaxis clara, hay algunas trampas comunes al trabajar con funciones tradicionales:


1. Olvidar los Paréntesis `()` al Definir o Llamar:

* Error: `function miFuncion { ... }` (al definir) o `console.log(miFuncion);` (al llamar sin ejecutar).
* Resultado: Error de sintaxis al definirla. Al llamarla sin paréntesis, no se ejecuta la función; en su lugar, se obtiene una referencia a la definición de la función misma (útil en otros contextos, pero un error si se busca ejecutarla).
* Solución: Siempre incluye los paréntesis: `function miFuncion() { ... }` y `console.log(miFuncion());`.

2. No Usar `return` cuando se Espera un Valor:

* Error:
        function sumar(a, b) {
          let suma = a + b;
          // ¡Falta el return!
        }
        let resultado = sumar(5, 3);
        console.log(resultado); // Muestra 'undefined'
* Resultado: La función se ejecuta, pero la variable `resultado` contendrá `undefined` porque la función no devolvió explícitamente ningún valor.
* Solución: Agrega `return` con el valor deseado: `return suma;`.

3. Malentendido del Ámbito (Scope) de las Variables:

* Error:
        function procesarDatos() {
          let datoLocal = "Soy local";
        }
        procesarDatos();
        console.log(datoLocal); // Error: datoLocal is not defined
* Resultado: Las variables declaradas con `let` o `const` (e incluso `var` antes de ES6) dentro de una función son *locales* a esa función. No son accesibles desde fuera de ella.
* Solución: Si necesitas el valor fuera de la función, debes devolverlo con `return` o pasarlo a otra función.

4. `this` Mal Entendido (Un Concepto Más Avanzado):

* Contexto: En funciones tradicionales, el valor de `this` (que se refiere al "contexto" de ejecución actual) es *dinámico*. Depende de *cómo* se llama la función, no de dónde se define.
* Problema: Esto puede llevar a confusión en contextos de objetos o callbacks, donde `this` podría no referirse al objeto que esperas.
* Ejemplo de confusión:
        const persona = {
          nombre: "Ana",
          saludar: function() { // Función tradicional
            console.log(`Hola, soy ${this.nombre}`); // 'this' se refiere a 'persona' aquí
            setTimeout(function() { // Función callback tradicional
              console.log(`Dentro de setTimeout: Hola, soy ${this.nombre}`); // ¡Aquí 'this' probablemente es 'window' o 'undefined' en modo estricto!
            }, 100);
          }
        };
        persona.saludar();
* Resultado: El primer `console.log` funciona bien, pero el segundo `console.log` dentro del `setTimeout` probablemente imprimirá "Hola, soy undefined" o "Hola, soy [nombre de la ventana]" porque `this` perdió su contexto original.
* Solución (parcial aquí, pero importante para diferenciar): Para mantener el `this` del contexto exterior, a menudo se usaba `const self = this;` o se recurría a las funciones flecha (`=>`) que tienen un `this` léxico (lo toman del entorno donde fueron definidas).

5. Errores de Tipos o Cantidad de Argumentos:

* Error: Llamar a una función con menos o más argumentos de los esperados, o con tipos de datos incorrectos.
* Ejemplo: `sumarNumeros(a, b)` y luego llamar `sumarNumeros(5)` (falta `b`) o `sumarNumeros(5, "tres")` (tipo incorrecto).
* Resultado: `NaN` (Not a Number) si se realizan operaciones matemáticas con `undefined` o tipos incompatibles, o errores lógicos difíciles de depurar.
* Solución: Implementa validación de parámetros dentro de tus funciones (como en el ejemplo `calcularTotalPedido`) o utiliza TypeScript para un control de tipos más estricto.

---


Dominar las funciones tradicionales es un paso fundamental para escribir código JavaScript efectivo y mantenible. ¡Sigue practicando y experimentarás su poder en tus proyectos de React y Node!