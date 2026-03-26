# Ejercicio 1: Formulario de Automóvil - Vue 3

Este proyecto es una aplicación web interactiva desarrollada con **Vue 3** y **Vite** para la gestión de registros de automóviles. Permite capturar datos técnicos, validarlos en tiempo real y visualizar un historial de capturas.

---

## 🛠️ Comandos de Instalación e Investigación

A continuación se explican los comandos necesarios para configurar y ejecutar el entorno de desarrollo:

### 1. `npm install`
Es el comando principal de **Node Package Manager (NPM)**. Su función es leer el archivo `package.json` del proyecto y descargar todas las dependencias y librerías necesarias (como Vue y Vite) en una carpeta llamada `node_modules`. 
* **¿Por qué es necesario?** Sin estas librerías, el código de Vue no puede ser interpretado por el navegador.

### 2. `npm run dev`
Este comando inicia el **servidor de desarrollo local** de Vite. Proporciona una URL (normalmente `http://localhost:5173/`) donde puedes ver los cambios en tu código en tiempo real gracias al **Hot Module Replacement (HMR)**.
* **Nota:** Es el comando que solicita la rúbrica para verificar que el proyecto corre sin errores.

### 3. `npm run build`
Se utiliza para preparar la aplicación para producción. Vite compila y optimiza todo el código (JavaScript, CSS, imágenes) y lo coloca en una carpeta llamada `dist`. Este código está listo para ser subido a un servidor web real.

---

## 🚀 Requisitos del Ejercicio

- **v-model:** Vinculación bidireccional de datos en todos los inputs.
- **Validación:** El campo de año cuenta con una restricción mínima de **1900**.
- **Reactividad:** Los datos capturados se muestran mediante **interpolación `{{ }}`** de forma instantánea.
- **Limpieza de datos:** Función dedicada para resetear el objeto `auto` a su estado original.
- **Prevenir recarga:** Uso de `@submit.prevent` para manejar el envío de forma asíncrona.

---

**Desarrollado por:** [Dora Itzel]  
**Materia:** Infraestructura y Persistencia (Unidad 3)