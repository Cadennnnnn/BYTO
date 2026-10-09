# BYTO — Propuesta funcional inicial

> **Propuesta abierta a mejoras, ampliaciones y perfeccionamiento durante el desarrollo.**  
> Documento de alcance funcional preliminar. Las funciones descritas son propuestas y no implican que ya estén implementadas.

## 1. Objetivo

Desarrollar una aplicación móvil para apoyar la gestión de inventario de múltiples tiendas o bodegas, permitiendo registrar conteos y movimientos de productos, detectar diferencias de stock y generar información útil para prevenir quiebres de inventario.

## 2. Funcionalidades por perfil

### 2.1 Operador

- **Escáner de productos:** leer códigos de barras de productos existentes y detectar códigos que todavía no estén registrados en el catálogo.
- **Registro de inventario:** escanear un producto, consultar sus datos y registrar la cantidad física contada.
- **Informe diario:** consultar un resumen de los productos escaneados, cantidades registradas y movimientos realizados durante el turno.
- **Escaneo programado:** ejecutar conteos de inventario según una fecha, horario o turno asignado.
- **Registro de diferencias:** informar discrepancias entre la cantidad física y el stock registrado en el sistema.
- **Registro de movimientos:** ingresar movimientos de entrada, salida o ajuste, según los permisos del usuario.

### 2.2 Administrador

- **Registro de operadores:** crear y mantener los perfiles de los operadores.
- **Registro de jefes de tienda o bodega:** administrar los perfiles de responsables de cada sucursal.
- **Registro de sucursales:** crear y mantener las tiendas o bodegas disponibles.
- **Gestión de productos:** registrar y actualizar nombre, código de barras, código interno, categoría y stock mínimo.
- **Informes generales:** consultar inventario, movimientos y diferencias de stock de las distintas sucursales.
- **Gestión de permisos:** definir qué acciones puede realizar cada perfil de usuario.

### 2.3 Jefe de tienda o bodega

- **Gestión de turnos:** crear turnos de inventario y asignar operadores responsables.
- **Planificación de inventarios:** programar conteos por fecha, área, categoría o grupo de productos.
- **Informes de stock:** identificar productos con stock bajo o próximos a agotarse.
- **Control de mermas:** registrar pérdidas, productos dañados, vencimientos y diferencias detectadas durante el conteo.
- **Alertas de reposición:** identificar productos que necesitan reposición para reducir el riesgo de quiebre de stock.
- **Supervisión de operadores:** revisar el avance de los conteos y las diferencias informadas.

## 3. Funcionalidades futuras

Estas funciones pueden incorporarse en etapas posteriores, dependiendo del tiempo disponible, la complejidad técnica y los requisitos de evaluación:

- Sincronización con una API REST para compartir información entre sucursales.
- Historial de auditoría con usuario, fecha, tipo de movimiento y cambios realizados.
- Exportación de informes a Excel o PDF.
- Notificaciones de stock bajo.
- Panel de indicadores para comparar sucursales, movimientos y diferencias.
- Gestión avanzada de turnos, tareas pendientes y planificación de conteos.

## 4. Alcance recomendado para el MVP académico

Para mantener el proyecto realizable y demostrar una base técnica sólida, se recomienda priorizar:

1. Selección de sucursal activa.
2. Consulta y búsqueda de productos.
3. Escaneo de códigos de barras.
4. Registro de cantidades y movimientos de inventario.
5. Validación de datos ingresados.
6. Persistencia local con Room.
7. Consulta del historial de movimientos.
8. Detección básica de productos bajo el stock mínimo.

Las funciones de administración avanzada de usuarios, asignación de turnos y control detallado de mermas pueden desarrollarse después de que el flujo principal esté operativo.

## 5. Flujo principal propuesto

1. El usuario ingresa a la aplicación.
2. Selecciona la sucursal o bodega en la que trabajará.
3. Accede al escáner o busca un producto manualmente.
4. La aplicación identifica el producto y muestra sus datos disponibles.
5. El operador ingresa la cantidad contada o registra el movimiento correspondiente.
6. La aplicación valida los datos y guarda el registro.
7. El usuario consulta el resultado y, cuando corresponda, las diferencias o alertas de stock.

## 6. Consideraciones técnicas

- **Plataforma:** Android.
- **Lenguaje y UI:** Kotlin y Jetpack Compose.
- **Arquitectura propuesta:** MVVM, con separación entre interfaz, lógica y acceso a datos.
- **Persistencia local:** Room.
- **Integración remota:** API REST, cuando esté definido el contrato del servicio.
- **Recurso nativo prioritario:** cámara para escaneo de códigos de barras.
- **Trazabilidad:** registrar fecha, tipo de movimiento y usuario asociado cuando el modelo de datos lo permita.

> **Dependencia pendiente:** NO PUEDO RESPONDER CON PRECISIÓN: falta el contrato de la API REST. Por ello, los endpoints y el formato definitivo de intercambio de datos deben definirse antes de implementar la integración.

## 7. Supuestos y riesgos

- Esta propuesta amplía las funciones descritas en el caso original; no todas necesariamente forman parte de los requisitos obligatorios de la evaluación.
- El escaneo de productos nuevos debe distinguir entre detectar un código desconocido y autorizar la creación de un producto en el catálogo.
- La gestión de usuarios y permisos requiere definir autenticación y reglas de acceso.
- La sincronización entre sucursales depende de la API REST y de cómo se resuelvan los conflictos de datos.
- Los informes deben basarse en movimientos e inventarios registrados; no deben presentarse como datos reales si se usan datos de prueba.
- Las funciones descritas son objetivos propuestos, no evidencia de implementación.

## 8. Criterios iniciales de aceptación

- El usuario puede seleccionar una sucursal activa.
- El operador puede buscar o escanear un producto y consultar su información.
- El sistema valida que las cantidades ingresadas sean válidas.
- El registro de inventario o movimiento queda guardado localmente.
- El usuario puede consultar los registros realizados.
- El sistema identifica productos bajo el stock mínimo cuando existen datos suficientes.
- La interfaz comunica errores y resultados de forma clara.

## 9. Evolución del proyecto

La aplicación se puede perfeccionar de manera incremental. Primero debe funcionar correctamente el flujo central de inventario; luego se pueden agregar administración de perfiles, turnos, informes avanzados, alertas y sincronización remota. Cada ampliación debe mantener la separación por capas, las validaciones y el historial de cambios.

---

**Estado del documento:** propuesta funcional preliminar.  
**Nombre de trabajo:** BYTO — *Inventario en movimiento*.
