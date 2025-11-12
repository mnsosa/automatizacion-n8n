# 🤖 n8n - Template "Traer Emails" (Gmail)

Este repositorio contiene un template sencillo de n8n para traer correos de Gmail y generar embeddings con OpenAI, guardándolos en una memoria vectorial en memoria (no persistente). Es ideal como base para pruebas de RAG o para explorar tus emails recientes.

## 📁 Estructura

- `compose.yml`: definición de Docker para levantar n8n
- `templates/traer_emails.json`: workflow listo para importar en n8n

## 📋 Requisitos

- Docker y el comando `docker compose`
- Una cuenta de Gmail para autorizar el acceso (OAuth2)
- Una API Key de OpenAI

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
   - OpenAI API (para el nodo `Embeddings OpenAI`)

## 🧠 ¿Qué hace el workflow?

- Lee hasta 10 emails no leídos desde Gmail (incluye spam y papelera por defecto).
- Carga los encabezados como documento.
- Genera embeddings con OpenAI.
- Inserta los vectores en un Vector Store en memoria (no se persiste entre ejecuciones).

## 🔧 Personalización rápida

- En el nodo `Get many messages` puedes cambiar:
  - `limit`: cantidad de correos (p. ej. 50)
  - `filters.readStatus`: `unread` o `all`
  - `filters.includeSpamTrash`: activar/desactivar
- Para persistencia, reemplaza el `Vector Store In Memory` por un almacén persistente compatible.
- Para indexar cuerpo de los emails, adapta el `Default Data Loader` a `{{$json.body}}` u otro campo.

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
