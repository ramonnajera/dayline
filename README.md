# Dayline DPDU - Plantillas de Correo

Este repositorio contiene el código fuente y los recursos gráficos para los correos informativos de **Dayline DPDU**, el evento bimestral de presentaciones y prototipos del equipo de desarrollo del Departamento de Plataformas Digitales Universitarias.

## 📁 Estructura del Proyecto

Para mantener el orden y un historial de todas las invitaciones, el proyecto está estructurado mediante **carpetas numeradas**. Cada número representa una edición del evento Dayline.

```text
dayline/
├── 1/                        # Primera edición del Dayline
│   ├── imagenes/             # Assets exclusivos de esta edición
│   │   ├── image 10.png
│   │   └── image 13.png
│   └── dayline-correo.html   # Código fuente del correo
├── 2/                        # Segunda edición (Próximamente)
│   ├── imagenes/
│   └── dayline-correo.html
└── README.md
```

## 📝 Flujo de Trabajo para Nuevas Ediciones

Cuando se acerque un nuevo Dayline, no es necesario empezar desde cero. Sigue estos pasos para crear el correo de la siguiente edición:

1. **Crear la nueva carpeta:** Duplica la carpeta de la última edición (por ejemplo, copia la carpeta `1/` y renómbrala a `2/`).
2. **Actualizar gráficos:** Dentro de la nueva carpeta `2/imagenes/`, elimina las imágenes viejas y sube las nuevas.
3. **Actualizar el HTML:** Abre el archivo `.html` de tu nueva carpeta y modifica los textos correspondientes.
4. **Actualizar las rutas de las imágenes (¡Importante!):** Asegúrate de cambiar el número de la carpeta en las URLs de las imágenes dentro de tu código HTML. 
   * *Ejemplo anterior:* `.../main/1/imagenes/imagen.png?raw=true`
   * *Nuevo ejemplo:* `.../main/2/imagenes/nueva-imagen.png?raw=true`

## 🛠️ Consideraciones Técnicas

Desarrollar correos HTML tiene reglas muy distintas al desarrollo web tradicional. Para garantizar que el equipo reciba el correo correctamente:

### 1. Alojamiento de Imágenes (Anti-Bloqueo)
No se utilizan servicios gratuitos de terceros debido a sus políticas de bloqueo contra *hotlinking* en clientes de correo. Todas las imágenes se sirven directamente desde este repositorio. 
*   Para obtener el enlace directo de una imagen nueva, ábrela en GitHub y copia la URL del archivo "Raw" (debe contener `raw=true` o empezar con `raw.githubusercontent.com`).

### 2. Tipografía y Compatibilidad (El "Bug" de Outlook)
El correo utiliza Google Fonts para mantener la identidad visual moderna:
*   **Títulos:** `Rubik` (Pesos 600, 900)
*   **Cuerpo:** `Noto Sans` (Pesos 400, 600, 700)

Dado que plataformas como Outlook de escritorio bloquean fuentes externas web y tienen un fallo crítico que convierte todo el texto a *Times New Roman*, el `<head>` del HTML incluye código condicional de Microsoft (`<!--[if mso]>`). Este código obliga a Outlook a ignorar las fuentes web y renderizar todo en `Arial, Helvetica, sans-serif`, asegurando que la estructura no se rompa para los usuarios de Windows.

## 🚀 Despliegue y Control de Versiones

La autenticación para operaciones de Push/Pull en este proyecto local se realiza mediante **llaves SSH** (`ed25519`), lo que elimina la necesidad de usar contraseñas.
*   **URL Remota:** `git@github.com:ramonnajera/dayline.git`

---
*Desarrollado para el equipo DPDU.*