# 🤖 n8n - Template "Traer Emails" (Gmail)

Este repositorio contiene un template sencillo de n8n para traer correos de Gmail filtrando por una palabra clave con el parámetro `q` de Gmail. Incluye un nodo `Set` para exponer campos útiles como `Subject`, `From` y `labels`.

## 📁 Estructura

- `compose.yml`: definición de Docker para levantar n8n
- `templates/traer_emails.json`: workflow listo para importar en n8n

## 📋 Requisitos

- Docker y el comando `docker compose`
- Una cuenta de Gmail para autorizar el acceso (OAuth2)

## 🚀 Puesta en marcha

1) Arranca n8n con Docker desde la raíz del proyecto:

```bash
docker compose up -d
```

2) Abre `http://localhost:5678` en tu navegador.

## 📥 Importar el template

1) En n8n, ve a "Workflows" → "Import from File".
2) Selecciona `templates/traer_emails.json`.
3) Reasigna las credenciales cuando te lo pida:
   - Gmail OAuth2 (para el nodo `Get many messages`)

## 🧠 ¿Qué hace el workflow?

- Busca mensajes en Gmail según `q` (por defecto: "jetsmart"), incluyendo leídos y no leídos (`readStatus: both`).
- No incluye spam ni papelera por defecto (`includeSpamTrash: false`).
- Limita los resultados a `limit = 10`.
- Usa un nodo `Set` para exponer campos: `Subject`, `From` y `labels`.

## 🔧 Personalización rápida

- En el nodo `Get many messages` puedes cambiar:
  - `limit`: cantidad de correos (p. ej., 50)
  - `filters.q`: palabra o frase a buscar (asunto/cuerpo)
  - `filters.readStatus`: `unread`, `read`, `both` o `all`
  - `filters.includeSpamTrash`: activar/desactivar
- En el nodo `Set` puedes ajustar qué campos exponer (por ejemplo, agregar `To`, `Date`, etc.).

## 🛠️ Comandos útiles

```bash
# Ver estado de los contenedores
docker compose ps

# Ver logs
docker compose logs -f

# Detener y limpiar
docker compose down
```

## ⚙️ Notas de configuración

El archivo `compose.yml` expone n8n en el puerto 5678 y configura la zona horaria `America/Argentina/Buenos_Aires`. Los datos se persisten en el volumen `n8n_data` del contenedor.
