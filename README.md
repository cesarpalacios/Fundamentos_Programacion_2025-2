# PROYECTO FINAL: FUNDAMENTOS DE PROGRAMACIÓN
**Universidad Nacional de Colombia - Sede Manizales**

**Asignatura:** Fundamentos de Programación

**Valor:** 30% de la Nota Final

**Modalidad:** Individual

---

## 1. CONTEXTO DEL PROYECTO: "CINE UNAL"

Usted ha sido contratado para desarrollar el sistema de gestión de reservas para la sala de cine universitaria. Debido a restricciones de hardware, el sistema debe ser eficiente en el manejo de memoria y debe guardar la información en archivos de texto para no perder las reservas si se apaga el computador.

**El objetivo:** Desarrollar una aplicación en C++ que gestione una sala con una distribución de sillas de **5 Filas x 6 Columnas**, utilizando programación modular, matrices y persistencia de datos.

---

## 2. REQUERIMIENTOS TÉCNICOS

El incumplimiento de cualquiera de las siguientes restricciones técnicas conllevará una penalización en la nota, ya que el objetivo es evaluar temas específicos del curso.

### A. Estructuras de Datos (Matrices Paralelas)
Usted debe gestionar la información sincronizando dos matrices globales:

1.  `int estado[5][6];`
    * Almacenará un `0` si la silla está **Libre**.
    * Almacenará un `1` si la silla está **Ocupada**.
2.  `string titulares[5][6];`
    * Almacenará el **Nombre del Cliente** que reservó.
    * Si la silla está libre, esta posición debe contener el texto `"---"`.

### B. Persistencia (Archivos de Texto)
El programa debe interactuar con dos archivos:

1.  **`sala.txt` (Lectura/Escritura):** Al iniciar el programa, se debe cargar la matriz de ceros y unos desde este archivo. Al salir, se debe guardar el estado actual.
2.  **`reporte.txt` (Solo Escritura - Append):** Cada vez que se haga una reserva exitosa, el programa debe agregar una línea nueva en este archivo con el formato: `Fecha - Silla reservada - Nombre`.

### C. Buenas Prácticas
* **Modularidad:** El `main()` debe ser corto y solo controlar el menú. Toda la lógica debe estar en funciones (Ej: `void mostrarSala()`, `void reservar()`).
* **Orden:** Código debidamente indentado y comentado.

---

## 3. FUNCIONALIDADES DEL MENÚ

El programa debe ejecutarse en un ciclo repetitivo mostrando las siguientes opciones:

1.  **Ver Sala:**
    * Debe dibujar la matriz en consola.
    * Si la silla está libre (0), muestre `[ L ]`.
    * Si la silla está ocupada (1), muestre `[ XX ]`.
2.  **Reservar Asiento:**
    * Solicite Fila (0-4) y Columna (0-5).
    * **Validación:** Si la silla ya está ocupada, debe mostrar un error y no permitir la reserva.
    * Si está libre, pida el Nombre, marque la silla con `1` en la matriz de estado y guarde el nombre en la matriz de titulares.
3.  **Cancelar Reserva:**
    * Solicite coordenadas. Valide que la silla esté ocupada.
    * Libere la silla (ponga `0` en estado y `"---"` en titulares).
4.  **Buscar Cliente:**
    * El usuario ingresa un nombre exacto.
    * El programa recorre la matriz de `titulares` y muestra qué silla(s) tiene reservada esa persona (Fila y Columna).
5.  **Guardar y Salir:**
    * Vuelca los datos de la memoria RAM al archivo `sala.txt` y termina la ejecución.

---

## 4. INFORME ESCRITO - OBLIGATORIO

Para validar la autoría y comprensión del código, debe entregar un documento PDF respondiendo las siguientes preguntas basadas en **SU** código.
**Nota:** Si el código funciona pero el informe es incoherente o generado por IA, la nota del trabajo será afectada drásticamente.

1.  **Diagrama de Memoria:**
    * Dibuje cómo se ven las dos matrices (`estado` y `titulares`) en la memoria RAM cuando el cliente "Ana" reserva la fila 0, columna 0. Indique qué valor exacto hay en `estado[0][0]` y qué valor hay en `titulares[0][0]`.
2.  **Manejo de Archivos:**
    * Copie el fragmento de código donde lee el archivo `sala.txt`. Explique: ¿Qué hace su programa la **primera vez** que se ejecuta en un computador nuevo donde el archivo `sala.txt` aún no existe? ¿Cómo evita que el programa se cierre por error?
3.  **Lógica de Cadenas:**
    * En la función "Buscar Cliente", explique qué instrucción utilizó para comparar el nombre buscado con los nombres en la matriz. ¿Por qué no es recomendable usar simplemente `if (nombre1 == nombre2)` en todos los entornos de C++?
4.  **Coherencia de Datos:**
    * Explique con sus palabras: ¿Cómo garantiza su programa que el nombre "Juan" no termine asignado a una silla que en la matriz de estado aparece como "Libre"? ¿En qué línea de código se aseguran ambas asignaciones?

---

## 5. ENTREGABLES

Debe subir a la plataforma (Moodle) un **único archivo comprimido** (`.zip` o `.rar`). La estructura interna de este archivo debe ser exactamente la siguiente:

1.  **Carpeta del Proyecto:** Una carpeta que contenga el código fuente (`.cpp`), archivos de cabecera (si los usa) y los archivos de texto (`.txt`) necesarios para correr el programa.
2.  **Informe Escrito:** El documento con las respuestas debe estar **fuera de la carpeta del código**, en la raíz del archivo comprimido.
3.  **Formato del Informe:** Únicamente se acepta formato **.PDF**. No se calificarán informes en Word (`.doc`), páginas (`.pages`) o enlaces a Drive.

**Estructura visual del entregable:**

```text
Entregable_ApellidoNombre.zip
│
├── Informe_Ingenieria.pdf      <-- (OBLIGATORIO .PDF)
│
└── Carpeta_Codigo_Fuente/      <-- (Carpeta con el programa)
    ├── main.cpp
    ├── funciones.cpp
    └── sala.txt
```

## 6. CRITERIOS DE EVALUACIÓN

| Criterio | Porcentaje | Descripción |
| :--- | :---: | :--- |
| **Persistencia (Archivos)** | 30% | El programa guarda y carga datos correctamente sin perder información al reiniciar. |
| **Lógica de Matrices** | 25% | Validaciones correctas (no sobreescribir reservas), manejo de índices y recorridos. |
| **Funcionalidad General** | 15% | El menú funciona, las búsquedas son correctas y no hay errores de ejecución. |
| **Orden y Estilo** | 10% | Código modular, uso de funciones, variables con nombres descriptivos. |
| **Informe de Ingeniería** | 20% | Respuestas técnicas precisas que demuestran dominio total del código escrito. |

## ## 7. FECHA MÁXIMA DE ENTREGA

* **Fecha Límite:** 12 de Diciembre de 2025.
* **Hora:** Hasta las 23:59 (Hora del servidor de la plataforma).
* **Política de Retrasos:** Dado que el semestre finaliza inmediatamente después de esta fecha, **NO se aceptarán entregas extemporáneas** ni envíos por correo electrónico. Se recomienda subir el archivo al menos 2 horas antes para evitar inconvenientes técnicos de último momento.
