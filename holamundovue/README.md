# Investigación de Comandos y Flujo de Trabajo (Vue 3 + Vite)

Este documento detalla el proceso de inicialización, instalación y ejecución del proyecto **holamundovue**, respondiendo a los puntos de investigación técnica de la Unidad 3.

---

## 1. Inicialización del Proyecto
**Comando ejecutado:** `npm create vite@latest holamundovue -- --template vue`

* **¿Qué hace exactamente?** Este comando utiliza la herramienta de andamiaje de **Vite** para crear una estructura de carpetas predefinida. No solo crea una carpeta, sino que descarga un "esqueleto" funcional de una aplicación moderna.
* **¿Por qué usamos `--template vue`?** Vite es agnóstico al framework (puede usarse con React, Svelte, o Vanilla JS). El flag `--template vue` le indica a Vite que instale la configuración específica para Vue 3, incluyendo el compilador de Componentes de Archivo Único (SFC) y los plugins necesarios para que el navegador entienda archivos `.vue`.

---

## 2. Instalación de Dependencias
**Comando ejecutado:** `npm install` (dentro del directorio `holamundovue`)

* **Dependencias instaladas:** Al ejecutar este comando, se crea la carpeta `node_modules` con las siguientes librerías clave:
    * **`vue`**: El núcleo del framework.
    * **`vite`**: El motor de construcción y servidor de desarrollo.
    * **`@vitejs/plugin-vue`**: El plugin que permite a Vite procesar los archivos de Vue.
    * **`eslint` / `prettier`**: (Opcionales) Para mantener la calidad y formato del código.

---

## 3. Ejecución y Servidor de Desarrollo
**Comando ejecutado:** `npm run dev`

* **Puerto del servidor:** Por defecto, el servidor de desarrollo corre en el **puerto 5173** (accesible en `http://localhost:5173/`).
* **¿Qué es "Hot Module Replacement" (HMR)?** Es una característica de Vite que permite actualizar módulos del código en el navegador **sin necesidad de recargar la página completa**. 
    * **Ventaja:** Si cambias un color en el CSS o un texto en el `App.vue`, el cambio se ve instantáneamente manteniendo el estado de la aplicación (por ejemplo, no se borran los datos que ya escribiste en un formulario).

---

## 4. Implementación del Hola Mundo
Se modificó el archivo `src/App.vue` para limpiar el contenido por defecto y utilizar la técnica de **interpolación**:

```javascript
// En el script:
data() {
  return {
    mensaje: "Hola Mundo desde Vue"
  }
}

// En el template:
<h1>{{ mensaje }}</h1>
**Desarrollado por:** [Dora Itzel]  
**Materia:** Infraestructura y Persistencia (Unidad 3)