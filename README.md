# Pulpeando · App del cliente

La app con la que el cliente de una pulpería pide a domicilio, ve su fiado y
su señal en la Central Pulpeando. Es una PWA en HTML/JS planos, sin build:
se publica tal cual con GitHub Pages desde la rama `main`, carpeta raíz.

Antes vivía en `pulpeando_interno/cliente/`. Se separó para que el sistema
del negocio no viaje junto con la app pública.

## Archivos

| Archivo | Qué es |
|---|---|
| `index.html` | La app completa |
| `config.js` | URL de Supabase y la llave publishable (pública por diseño; nunca la service_role) |
| `instalar.js` | El botón de instalar la app (mismo archivo que en `pulpeando_interno`) |
| `sw.js` | Service worker: la cáscara abre sin internet; nada de Supabase se cachea |
| `manifest.webmanifest` + `icono-*.png` + `favicon.ico` | Para instalarla en el teléfono |

**Al cambiar cualquier archivo hay que subir la versión de la caché en
`sw.js`** (`pulpeando-cliente-vN`), o el teléfono sigue con la vieja.

## Instalar

En la portada y dentro de la app hay un botón «Instalar». En Chrome/Edge/
Samsung abre el cuadro de instalación del navegador; en iPhone explica cómo
con Compartir → Agregar a inicio. Abierta como app, el botón no aparece.

## Pruebas

```
npm install jsdom      # una sola vez
node pruebas.mjs       # la app, manejada como un cliente
node instalar.pruebas.mjs
```
