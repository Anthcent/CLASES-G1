# 🎓 CLASES-G1

Bienvenido al repositorio **CLASES-G1**. Este espacio está dedicado a la organización de materiales didácticos, ejercicios prácticos y recursos esenciales para la asignatura de Programación.

[![Estado](https://img.shields.io/badge/Estado-En_Desarrollo-green)](https://github.com/tu-usuario/CLASES-G1)
[![Actualizado](https://img.shields.io/badge/Actualizado-Diciembre_2025-blue)](https://github.com/tu-usuario/CLASES-G1)

---

## 📌 Descripción

Este repositorio sirve como punto central de conocimiento para estudiantes y mentores. Aquí encontrarás:

*   📘 **Material Teórico**: Explicaciones detalladas de conceptos clave.
*   🧪 **Ejercicios Prácticos**: Retos para afianzar lo aprendido.
*   🚀 **Ejemplos Reales**: Código profesional listo para estudiar.

## 📁 Estructura del Proyecto

Organización sugerida de directorios:

*   `docs/` — Documentación complementaria y guías.
*   `src/` — Código fuente y ejemplos por tema.
*   `exercises/` — Ejercicios propuestos y soluciones.
*   `assets/` — Recursos gráficos y estáticos.

---

## 🏗️ Guía de Aprendizaje: Funciones Tradicionales en JavaScript

Las funciones son el pilar de la modularidad en JavaScript. A continuación, profundizamos en las **Funciones Tradicionales**, esenciales para cualquier desarrollador JS/React/Node.

### 1. Concepto Fundamental

Una **función tradicional** es un bloque de código reutilizable. Piensa en ella como una máquina que procesa entradas (parámetros) y produce una salida (retorno).

**Ventajas Clave:**
*   **Modularidad**: Divide problemas complejos en partes manejables.
*   **DRY (Don't Repeat Yourself)**: Evita la duplicación de código.
*   **Contexto Dinámico**: Manejan su propio `this` (útil en ciertos patrones de diseño).

### 2. Anatomía de la Sintaxis

```javascript
/**
 * Nombre explicativo de la función
 * @param {tipo} nombreParametro - Descripción
 * @returns {tipo} Descripción del retorno
 */
function nombreDeLaFuncion(parametro1, parametro2) {
  // Lógica interna (Cuerpo de la función)
  const resultado = parametro1 + parametro2;
  
  // Retorno de valor
  return resultado; 
}
```

### 3. Ejemplo Profesional: Cálculo de Pedidos

Imagina un sistema de e-commerce real. Necesitamos calcular totales manejando impuestos y descuentos de forma robusta.

```javascript
/**
 * Calcula el precio total de un pedido de e-commerce.
 * Ideal para usar en carritos de compra o procesos de checkout.
 *
 * @param {Array<Object>} productos - Lista de productos { id, precio, cantidad }.
 * @param {number} [descuentoPorcentaje=0] - Descuento a aplicar (0-100).
 * @param {number} [impuestoPorcentaje=0] - Impuesto a aplicar (0-100).
 * @returns {number} Precio total final redondeado a 2 decimales (interno).
 */
function calcularTotalPedido(productos, descuentoPorcentaje = 0, impuestoPorcentaje = 0) {
  
  // A. VALIDACIÓN DEFENSIVA
  // Protegemos la función contra datos corruptos o vacíos.
  if (!Array.isArray(productos) || productos.length === 0) {
    console.warn("⚠️ Advertencia: Lista de productos vacía o inválida.");
    return 0;
  }

  let subtotal = 0;

  // B. CÁLCULO DE SUBTOTAL
  // Iteramos eficientemente sobre los productos.
  for (const producto of productos) {
    // Verificamos la integridad de cada producto individualmente.
    const esValido = producto 
                     && typeof producto.precio === 'number' 
                     && typeof producto.cantidad === 'number';

    if (esValido) {
      subtotal += producto.precio * producto.cantidad;
    } else {
      console.error(`❌ Producto corrupto omitido:`, producto);
    }
  }

  // C. APLICACIÓN DE DESCUENTOS
  // Usamos Math.max para asegurar que no haya porcentajes negativos.
  const factorDescuento = Math.max(0, descuentoPorcentaje) / 100;
  const montoDescuento = subtotal * factorDescuento;
  const subtotalConDescuento = subtotal - montoDescuento;

  // D. APLICACIÓN DE IMPUESTOS
  // El impuesto se calcula sobre el precio ya descontado.
  const factorImpuesto = Math.max(0, impuestoPorcentaje) / 100;
  const montoImpuesto = subtotalConDescuento * factorImpuesto;

  // E. RETORNO FINAL
  return subtotalConDescuento + montoImpuesto;
}

// --- CASOS DE USO ---

const carrito = [
  { id: 1, nombre: 'Laptop Dev', precio: 1200, cantidad: 1 },
  { id: 2, nombre: 'Monitor 4K', precio: 400, cantidad: 2 } // Total productos: 2000
];

// Caso 1: Compra estándar (10% descuento, 16% IVA)
// Cálculo: 2000 - 10% (200) = 1800 + 16% (288) = 2088
console.log("Total a Pagar:", calcularTotalPedido(carrito, 10, 16)); 
```

### 4. Trampas Comunes y Best Practices

| Error Común | Por qué sucede | Solución Profesional |
| :--- | :--- | :--- |
| **Olvidar el `return`** | La función ejecuta la lógica pero entrega `undefined`. | Siempre asegúrate de qué valor debe salir de tu función. |
| **Ignorar Tipos** | Sumar números con textos (`5 + "5" = "55"`). | Valida los inputs al inicio de la función. |
| **Confusión con `this`** | En callbacks, `this` puede perder su referencia original. | Usa *Arrow Functions* para callbacks o `bind()`. |
| **Función "Dios"** | Una función que hace 10 cosas a la vez. | Una función debe hacer **una** sola cosa bien (Principio de Responsabilidad Única). |

---

## 🛠️ Instalación y Uso Local

Para clonar y probar este repositorio en tu máquina:

```bash
# 1. Clonar el repositorio
git clone https://github.com/tu-usuario/CLASES-G1.git

# 2. Entrar al directorio
cd CLASES-G1

# 3. (Opcional) Instalar dependencias si existen
npm install
```

---

<p align="center">
  <sub>Desarrollado con ❤️ para la clase de Programación G1</sub>
</p>