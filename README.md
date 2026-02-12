# Lab4

## Parte 1 – Modo Offline Elegante (Graceful Offline Mode)

###  Descripción

En esta parte se implementó un manejo de errores alineado con una arquitectura **Offline-First**, mejorando la experiencia de usuario cuando ocurre un fallo de red.

La aplicación ahora:

- Muestra datos en caché cuando están disponibles, incluso si ocurre un error de red.
- Presenta un Snackbar no bloqueante para errores de red.
- Solo muestra un error en pantalla completa cuando NO existen datos en caché.
- Permite reintentar la operación sin perder la vista actual ni los datos mostrados.

Esto garantiza que la UI nunca se quede en un estado inconsistente y que el usuario siempre vea la información disponible en la base de datos local.

---

### Video explicativo

Video explicación: https://youtu.be/wvkaScyyFjk

---

### ✅ Definition of Done (DoD)

- [x] **UiState actualizado** – El estado `Error` acepta `List<Amiibo>?` opcional.
- [x] **Datos en caché preservados** – El estado de error mantiene los datos existentes.
- [x] **Snackbar mostrado** – El error de red muestra un Snackbar en lugar de un error de pantalla completa.
- [x] **Grid visible** – El usuario puede seguir viendo los Amiibos en caché mientras se muestra el Snackbar.
- [x] **Error completo solo si está vacío** – El error en pantalla completa solo aparece si `data` es null o está vacío.
- [x] **Reintento disponible** – El Snackbar incluye botón "Retry".
- [x] **Dismiss funcional** – El Snackbar puede cerrarse sin afectar el grid.

---

# Parte 2 – Búsqueda Local Reactiva

## Implementación

Se desarrolló una búsqueda local que:

- Agrega un `OutlinedTextField` en la parte superior de la pantalla.
- Filtra los Amiibos en tiempo real conforme el usuario escribe.
- Utiliza una consulta SQL de Room (no filtrado en memoria).
- Cambia entre la lista completa y la lista filtrada de manera reactiva usando `flatMapLatest`.

---

### Video explicativo

Video explicación: https://youtu.be/OAbyyn9a7aI

---

### ✅ Definition of Done (DoD)

- [x] **Método en DAO existente** – `searchAmiibos(query: String): Flow<List<AmiiboEntity>>`.
- [x] **Consulta LIKE funcional** – SQL usa `WHERE name LIKE '%' || :query || '%'`.
- [x] **Search TextField** – `OutlinedTextField` ubicado en la parte superior.
- [x] **Filtrado en tiempo real** – Los resultados se actualizan mientras el usuario escribe.
- [x] **Cambio de Flow reactivo** – Se utiliza `flatMapLatest` para alternar entre flows.
- [x] **Consulta vacía = lista completa** – Cuando el campo está vacío se muestra toda la lista.
- [x] **Botón limpiar** – Ícono "X" para borrar el texto de búsqueda.

---
