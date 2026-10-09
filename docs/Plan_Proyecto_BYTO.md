# BYTO — Plan de proyecto

**Aplicación móvil de inventario multi-tienda con escaneo de códigos de barras**  
**Asignatura:** DSY1105 — Desarrollo de Aplicaciones Móviles  
**Institución:** Duoc UC — CITT  
**Estado del documento:** propuesta de planificación; debe actualizarse a medida que se confirmen e implementen las decisiones.

> **Importante:** este documento describe el alcance propuesto. No significa que las funcionalidades, integraciones o tecnologías estén implementadas. Las funciones avanzadas se deben priorizar según el tiempo disponible y las pautas EP2 y EP3.

## 1. Visión del proyecto

BYTO es una aplicación Android orientada a facilitar el registro y la consulta de inventario en distintas tiendas o bodegas. Busca reducir errores de digitación, agilizar los conteos físicos, registrar los movimientos de stock y ayudar a detectar diferencias o productos próximos a agotarse.

La aplicación se desarrollará como un MVP académico. Se trabajará con datos ficticios y no se conectará a sistemas productivos de empresas.

### 1.1 Problema que aborda

Cuando el inventario se controla mediante planillas o registros manuales, la información puede quedar desactualizada, se pueden duplicar registros y resulta difícil conocer las diferencias entre el stock físico y el registrado. BYTO propone centralizar los registros y facilitar su trazabilidad desde un dispositivo Android.

### 1.2 Objetivos

- Facilitar la identificación de productos mediante el escaneo de códigos de barras.
- Registrar conteos, entradas, salidas y ajustes de inventario.
- Consultar stock por tienda o bodega.
- Detectar diferencias de inventario y productos bajo el stock mínimo.
- Mantener un historial de movimientos que permita revisar qué se registró.
- Construir una aplicación organizada, validada y mantenible, usando MVVM y persistencia local con Room.
- Utilizar GitHub y Trello para documentar el trabajo y coordinar al equipo.

## 2. Usuarios y funcionalidades propuestas

### 2.1 Operador

- Seleccionar o confirmar la tienda/bodega en la que realizará el inventario.
- Escanear códigos de barras de productos existentes.
- Consultar los datos disponibles del producto identificado.
- Ingresar la cantidad física contada.
- Registrar movimientos permitidos: entrada, salida, ajuste o conteo.
- Corregir los datos antes de confirmar un registro.
- Consultar un resumen de los registros realizados durante su sesión o turno.
- Informar códigos no reconocidos o diferencias de stock.

**Regla para productos nuevos:** si el código escaneado no existe, la aplicación debe informar que no se encontró el producto. La creación de un producto nuevo debe estar autorizada para el perfil correspondiente; no se debe crear automáticamente un producto solo por escanear un código desconocido.

### 2.2 Administrador

- Registrar y mantener tiendas o bodegas.
- Registrar y mantener productos del catálogo.
- Registrar usuarios y asignar perfiles, si la gestión de usuarios queda dentro del alcance aprobado.
- Consultar informes consolidados de inventario y movimientos.
- Consultar el estado de las sucursales y las alertas de stock.

### 2.3 Jefe de tienda o bodega

- Revisar el stock de su tienda/bodega.
- Crear o coordinar turnos de inventario y asignar operadores, si esta función se incluye en la versión final.
- Revisar diferencias entre cantidades físicas y cantidades registradas.
- Consultar productos bajo el stock mínimo.
- Registrar o revisar mermas, como productos dañados, vencidos o pérdidas, si se define un tipo de movimiento y su validación.
- Solicitar o registrar necesidades de reposición.

### 2.4 Funciones futuras

Estas funciones son ampliaciones posibles y no deben retrasar el flujo principal:

- Administración avanzada de turnos y asignaciones.
- Gestión completa de usuarios y permisos.
- Informes avanzados y exportación a Excel o PDF.
- Notificaciones locales de stock bajo.
- Panel de indicadores comparativos entre sucursales.
- Sincronización remota y resolución de conflictos entre dispositivos.

## 3. Alcance recomendado del MVP

Para reducir el riesgo y llegar a una aplicación demostrable, se recomienda implementar primero el siguiente flujo:

1. Mostrar o seleccionar la tienda/bodega activa.
2. Consultar y buscar productos.
3. Escanear un código de barras con la cámara.
4. Mostrar los datos del producto identificado.
5. Ingresar y validar una cantidad.
6. Registrar un conteo o movimiento.
7. Guardar y volver a consultar los datos.
8. Mostrar el historial básico y señalar stock bajo el mínimo cuando los datos estén disponibles.

El escaneo de códigos de barras es un requisito importante del caso. Debe priorizarse frente a funciones más avanzadas como los turnos, los informes complejos o la administración completa de perfiles.

### 3.1 Fuera del alcance inicial

- Integración con ERP, POS u otros sistemas productivos.
- Uso de credenciales o información confidencial real.
- Garantizar operación offline completa si la fase exige conexión permanente.
- Implementar todas las funciones futuras antes de validar el flujo principal.
- Presentar datos de prueba como si fueran datos reales de una empresa.

## 4. Requisitos funcionales iniciales

| ID | Requisito | Prioridad | Criterio de aceptación inicial |
|---|---|---|---|
| RF-01 | Selección de tienda/bodega | Alta | El usuario puede elegir una ubicación disponible y la app muestra cuál está activa. |
| RF-02 | Consulta de productos | Alta | Se puede buscar un producto y ver sus datos básicos. |
| RF-03 | Escaneo de código de barras | Alta | La cámara permite leer un código compatible y buscar el producto correspondiente. |
| RF-04 | Manejo de código desconocido | Alta | La app informa que el código no está registrado y no crea productos sin autorización. |
| RF-05 | Registro de conteo | Alta | Se puede ingresar una cantidad válida y guardar el conteo. |
| RF-06 | Registro de movimientos | Alta | Se puede registrar el tipo de movimiento y la cantidad, con las validaciones definidas. |
| RF-07 | Persistencia | Alta | Los datos guardados siguen disponibles al volver a consultar o reiniciar la app, según la estrategia de almacenamiento definida. |
| RF-08 | Historial básico | Media-alta | Se pueden consultar movimientos registrados con fecha, producto y tipo. |
| RF-09 | Stock mínimo | Media-alta | La app identifica productos cuyo stock está en o bajo el mínimo configurado. |
| RF-10 | Validación de formularios | Alta | Los campos obligatorios y las cantidades inválidas muestran mensajes claros. |
| RF-11 | Informe diario | Media | Se muestra un resumen de registros realizados durante la jornada o sesión. |
| RF-12 | Turnos y mermas | Posterior | Se implementa solo si el tiempo y las pautas lo permiten. |

Las prioridades son una propuesta de planificación, no una modificación de la pauta oficial. Deben revisarse con el docente y el equipo.

## 5. Requisitos no funcionales

- **Usabilidad:** textos legibles, botones fáciles de tocar y mensajes de error comprensibles.
- **Accesibilidad:** contraste suficiente, soporte para tamaño de fuente del sistema y descripciones de contenido cuando corresponda.
- **Validación:** las reglas de negocio no deben depender exclusivamente de los componentes visuales.
- **Mantenibilidad:** separar interfaz, lógica de presentación y acceso a datos.
- **Trazabilidad:** conservar los datos necesarios para identificar cuándo se registró un movimiento y a qué tienda y producto corresponde.
- **Protección de datos:** usar datos sintéticos y no publicar secretos ni credenciales.
- **Robustez:** representar estados de carga, éxito, error y ausencia de resultados.
- **Compatibilidad:** probar la aplicación en el emulador o dispositivo Android disponible.

## 6. Modelo de datos conceptual

El modelo final debe ajustarse a los datos que entregue la API y a la implementación real. La siguiente lista es una propuesta conceptual.

### 6.1 Tienda o bodega

- Identificador.
- Código.
- Nombre.
- Tipo: tienda o bodega.
- Estado: activa o inactiva.

### 6.2 Producto

- Identificador.
- Código de barras.
- Código interno.
- Nombre.
- Categoría.
- Descripción, si está disponible.
- Estado.

### 6.3 Stock por tienda

El stock debe asociarse a una tienda o bodega, ya que un mismo producto puede tener cantidades diferentes en cada ubicación.

- Identificador de tienda.
- Identificador de producto.
- Stock actual.
- Stock mínimo.
- Fecha de actualización.

### 6.4 Movimiento de inventario

- Identificador.
- Tienda.
- Producto.
- Tipo: entrada, salida, ajuste o conteo.
- Cantidad registrada.
- Stock anterior y resultante, si el servicio los entrega o la arquitectura permite calcularlos de forma confiable.
- Fecha y hora.
- Identificador de usuario u operador anonimizado, si está disponible.
- Origen de captura: escaneo o ingreso manual, si se medirá esa diferencia.
- Motivo, especialmente para ajustes o mermas.

### 6.5 Usuario y roles

Si se implementan perfiles, se consideran inicialmente los roles Operador, Jefe de tienda/bodega y Administrador. La autenticación, el almacenamiento de credenciales y los permisos deben definirse antes de tratarlo como una función operativa. Para el MVP se puede usar un acceso simulado con datos ficticios si eso es suficiente para la evaluación.

### 6.6 Reglas de negocio propuestas

- Las cantidades ingresadas deben ser numéricas y respetar las reglas del tipo de movimiento.
- No se debe aceptar una cantidad negativa para un conteo físico.
- Una salida no debe dejar el stock bajo cero, salvo que el caso y el docente definan explícitamente otra regla.
- Un conteo compara la cantidad física con la cantidad registrada y permite mostrar la diferencia.
- Un producto debe tener un código de identificación válido; si el código de barras debe ser único, esa regla se valida al crear o editar productos.
- Una alerta de stock bajo se puede generar cuando el stock actual sea menor o igual al stock mínimo.
- Las correcciones relevantes deben quedar registradas según el modelo de historial que se implemente.

Estas reglas son propuestas y deben coincidir con el contrato de datos y la lógica real de la aplicación.

## 7. Arquitectura Android propuesta

**Tecnologías base:** Kotlin, Jetpack Compose, Material 3, MVVM, Coroutines y StateFlow, Room y CameraX con un lector de códigos de barras compatible.

Flujo arquitectónico:

```text
Pantalla Compose
      ↓ eventos del usuario
ViewModel
      ↓ casos de uso / lógica de aplicación
Repository
      ↓
Room (persistencia local) y/o API REST
```

### 7.1 Responsabilidades

- **UI (Compose):** muestra el estado y recoge acciones del usuario. Evita contener reglas de negocio.
- **ViewModel:** expone un estado de pantalla, procesa eventos y coordina las operaciones.
- **Domain o lógica de aplicación:** contiene las reglas de negocio y validaciones reutilizables. Para un MVP pequeño puede mantenerse sencillo, sin crear capas innecesarias.
- **Repository:** centraliza el acceso a datos y evita que la UI dependa directamente de Room o Retrofit.
- **Room:** proporciona persistencia local. Su función exacta —almacenamiento principal, caché o apoyo a la sincronización— debe decidirse de acuerdo con la pauta y la API.
- **API REST:** permite consultar o registrar datos remotos solo cuando se conozca el contrato real del servicio.

### 7.2 Estructura de carpetas sugerida

La estructura definitiva dependerá del proyecto creado en Android Studio. Como punto de partida:

```text
app/src/main/java/<paquete>/
├── data/
│   ├── local/
│   ├── remote/
│   └── repository/
├── domain/
│   ├── model/
│   └── usecase/
├── ui/
│   ├── navigation/
│   ├── components/
│   ├── screens/
│   └── theme/
└── viewmodel/
```

No es necesario crear todas las carpetas vacías al inicio. Se agregan a medida que se implementan las funciones.

### 7.3 Estado de interfaz

Cada pantalla relevante debería representar, según corresponda, estados como carga, contenido, error y lista vacía. La interfaz debe observar el estado expuesto por el ViewModel y no duplicar la lógica de validación.

## 8. Cámara y recursos nativos

El escaneo con cámara es un requisito central del caso. La implementación debe:

- Solicitar el permiso de cámara cuando sea necesario.
- Explicar por qué se requiere el permiso.
- Mostrar un estado comprensible si el usuario lo deniega.
- Leer códigos de barras compatibles con los productos de prueba.
- Permitir recuperarse de un código no reconocido.
- Ofrecer ingreso manual como alternativa si se define para el MVP.

Las notificaciones locales para alertas de stock pueden considerarse como un recurso nativo adicional, pero no deben priorizarse por encima del escaneo funcional y de los requisitos obligatorios de evaluación.

## 9. API REST: dependencia pendiente

El caso contempla comunicación con un backend Spring Boot mediante API REST, pero las rutas, los modelos JSON, la autenticación y las respuestas reales deben obtenerse del contrato entregado o acordado para el proyecto.

**NO PUEDO RESPONDER CON PRECISIÓN: falta el contrato de la API REST.**

Por ese motivo, no se deben presentar rutas como `/productos`, `/stock` o `/movimientos` como endpoints confirmados. Se pueden usar como ejemplos de diseño, claramente marcados como propuestas, después de acordarlo con el equipo y el docente.

Antes de integrar la API, confirmar:

- URL base para desarrollo.
- Endpoints y métodos HTTP.
- Parámetros y cuerpos de solicitud.
- Formatos de respuesta y errores.
- Autenticación, si aplica.
- Reglas de stock y validación del backend.
- Cómo se identifican la tienda, el producto y el usuario.
- Estrategia de persistencia y sincronización con Room.

## 10. Plan de trabajo alineado con EP2 y EP3

Las fechas y entregables concretos deben ajustarse al calendario oficial de la asignatura. No se asume que el equipo dispone de ocho semanas adicionales.

### Etapa 1 — Preparación y base

- Crear el repositorio GitHub.
- Incorporar README y documentos del proyecto.
- Crear el proyecto Android y verificar que compile.
- Definir navegación inicial, tema visual y pantallas principales.
- Acordar tareas y responsables en Trello.

### Etapa 2 — Base funcional para EP2

- Implementar navegación y formularios.
- Agregar validaciones y manejo de estado.
- Implementar persistencia local con Room según los requisitos.
- Incluir animaciones funcionales pertinentes.
- Integrar recursos nativos requeridos, priorizando la cámara y el escaneo.
- Probar los flujos principales y documentar el proyecto.
- Verificar cada indicador de la pauta EP2 con evidencia real.

### Etapa 3 — Preparación para EP3

- Asegurar que la aplicación se ejecute de forma estable.
- Profundizar en la lógica, arquitectura y persistencia.
- Preparar una demostración que evidencie cambios reales en los datos.
- Verificar permisos y funcionamiento del recurso nativo.
- Practicar la explicación individual del código, las decisiones técnicas y la colaboración.
- Ensayar posibles modificaciones en vivo sin depender de herramientas externas durante la defensa, de acuerdo con las instrucciones de evaluación.

### Etapa 4 — Mejoras posteriores, si hay tiempo

- Historial avanzado y filtros.
- Alertas más completas.
- Administración de usuarios, tiendas y turnos.
- Informes y exportación.
- Integración remota completa una vez confirmado el contrato de la API.

## 11. Organización del equipo, GitHub y Trello

El trabajo se desarrolla en pareja. La distribución final debe acordarse entre ambos integrantes; no se asume un equipo de tres o cuatro personas.

### 11.1 Distribución sugerida

- **Integrante A:** navegación, pantallas Compose, componentes visuales y formularios.
- **Integrante B:** modelo de datos, Room, repositorios y lógica de inventario.
- **Trabajo compartido:** integración, escáner, pruebas, revisión de código, README y preparación de la defensa.

Esta distribución no debe generar dependencia exclusiva de una persona: ambos integrantes deben comprender la arquitectura y poder explicar las decisiones del proyecto.

### 11.2 Flujo de GitHub

- Mantener el repositorio conforme a las instrucciones de la evaluación; si se exige visibilidad pública, verificar que esté configurada.
- Usar commits descriptivos y frecuentes.
- Evitar subir contraseñas, claves, datos personales o configuraciones locales sensibles.
- Revisar los cambios antes de integrarlos.
- Confirmar que el proyecto pueda clonarse y abrirse desde un entorno Android Studio.

Ejemplos de mensajes:

```text
docs: add BYTO functional proposal
feat: add inventory navigation
feat: validate stock count form
fix: handle unknown barcode
test: add inventory validation tests
```

### 11.3 Tablero Trello sugerido

Columnas:

`BACKLOG → POR HACER → EN DESARROLLO → REVISIÓN → PRUEBAS → LISTO`

Cada tarjeta debe incluir responsable, descripción, criterio de aceptación y evidencia cuando corresponda. Una tarea no se mueve a **LISTO** solo porque exista un diseño: debe estar implementada y comprobada según su criterio de aceptación.

## 12. Métricas de éxito propuestas

Las métricas solo se deben reportar si se implementa una forma reproducible de medirlas.

| Objetivo | Métrica propuesta | Consideración |
|---|---|---|
| Agilizar conteos | Tiempo promedio por producto | Comparar tareas equivalentes y registrar el método utilizado. |
| Reducir digitación | Proporción de registros realizados por escaneo | Requiere registrar el origen de captura. |
| Mejorar trazabilidad | Porcentaje de movimientos con producto, tienda, tipo y fecha | Depende de que esos campos existan y se guarden correctamente. |
| Detectar stock bajo | Cantidad de productos bajo el mínimo | Depende de disponer de stock actual y stock mínimo por tienda. |

No se deben afirmar porcentajes de mejora sin mediciones reales.

## 13. Riesgos y decisiones pendientes

| Tema | Riesgo o vacío | Acción recomendada |
|---|---|---|
| Contrato API REST | No se han confirmado rutas ni formatos | Obtener el contrato antes de implementar llamadas concretas. |
| Room y conexión permanente | Debe aclararse si Room es almacenamiento principal o caché | Validar la estrategia con la pauta y el docente. |
| Alcance del MVP | Usuarios, turnos, mermas e informes pueden ampliar demasiado el proyecto | Priorizar el flujo de inventario y dejar extras para después. |
| Escaneo | El permiso o la lectura pueden fallar | Manejar denegación, errores y códigos desconocidos; probar en dispositivo o emulador compatible. |
| Stock por tienda | El mismo producto puede tener cantidades distintas por sucursal | Modelar el stock asociado a tienda y producto. |
| Roles y autenticación | Un acceso simulado no equivale a seguridad de producción | Documentar el alcance académico y no usar credenciales reales. |
| Trabajo en pareja | Un integrante podría desconocer partes relevantes | Hacer revisiones compartidas y practicar la defensa individual. |
| Evidencia de evaluación | Mockups o documentación no demuestran funcionamiento | Verificar cada criterio en la aplicación ejecutándose. |

## 14. Checklist de avance

### Proyecto y documentación

- [ ] Repositorio GitHub creado y accesible.
- [ ] README con descripción, integrantes, funcionalidades e instrucciones.
- [ ] Propuesta funcional y documentos de apoyo guardados en `docs/`.
- [ ] Trello actualizado con tareas y responsables.
- [ ] Commits que reflejan avances reales.

### Aplicación

- [ ] El proyecto abre y compila en Android Studio.
- [ ] La navegación principal funciona.
- [ ] Los formularios validan los datos.
- [ ] El estado de pantalla refleja carga, éxito y error.
- [ ] Room guarda y recupera los datos requeridos.
- [ ] El escaneo de códigos de barras funciona y gestiona permisos.
- [ ] Las animaciones requeridas funcionan.
- [ ] Se han probado al menos los flujos principales.

### Evaluación

- [ ] Revisar los siete indicadores oficiales de EP2.
- [ ] Confirmar la ejecución estable antes de la presentación EP3.
- [ ] Ambos integrantes pueden explicar y modificar el código.
- [ ] El enlace de GitHub y la entrega en AVA cumplen las instrucciones docentes.

---

**Nombre de trabajo:** BYTO  
**Frase propuesta:** *Inventario en movimiento*  
**Estado:** planificación inicial, pendiente de confirmación del equipo y de contraste con las pautas oficiales.
