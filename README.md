# 🤖 n8n - Automatización sin código

## ¿Qué es n8n?

n8n es una herramienta que te permite **automatizar tareas** sin necesidad de programar. Piensa en ella como un asistente que puede conectar diferentes aplicaciones y hacer que trabajen juntas automáticamente.

### Ejemplos de lo que puedes hacer:
- 📧 Guardar automáticamente los adjuntos de tus emails en Google Drive
- 📊 Enviar notificaciones a Slack cuando lleguen nuevos datos a una hoja de cálculo
- 🔄 Sincronizar información entre diferentes aplicaciones
- ⏰ Programar tareas que se ejecuten automáticamente

## 📋 Requisitos previos

Antes de instalar n8n, necesitas tener instalado:
- **Docker**: Es como un contenedor que permite ejecutar aplicaciones de forma aislada y segura
- **Docker Compose**: Una herramienta que simplifica el manejo de aplicaciones en Docker

> 💡 **Nota**: Si no tienes Docker instalado, puedes descargarlo desde [docker.com](https://www.docker.com/get-started)

## 🚀 Instalación

### Paso 1: Descargar este proyecto

Descarga o clona este repositorio en tu computadora.

### Paso 2: Iniciar n8n

Abre una terminal en la carpeta del proyecto y ejecuta:

```bash
docker-compose up -d
```

Este comando:
- Descargará n8n (solo la primera vez)
- Creará un espacio para guardar tus automatizaciones
- Iniciará n8n en segundo plano

### Paso 3: Acceder a n8n

Una vez iniciado, abre tu navegador y ve a:

```
http://localhost:5678
```

¡Listo! Ya puedes empezar a crear tus automatizaciones.

## 🛠️ Comandos útiles

### Ver si n8n está funcionando
```bash
docker-compose ps
```

### Detener n8n
```bash
docker-compose down
```

### Reiniciar n8n
```bash
docker-compose restart
```

### Ver los logs (mensajes de n8n)
```bash
compose logs -f
```

## ⚙️ Configuración

La configuración de n8n está en el archivo `docker-compose.yml`. Allí puedes cambiar:
- La zona horaria (por defecto: America/Argentina/Buenos_Aires)
- El puerto de acceso (por defecto: 5678)

## 📚 Recursos adicionales

- [Documentación oficial de n8n](https://docs.n8n.io/)
- [Plantillas de automatizaciones](https://n8n.io/workflows/)
- [Comunidad de n8n](https://community.n8n.io/)

## ❓ Problemas comunes

### El puerto 5678 ya está en uso
Si ves un error sobre el puerto, puedes cambiarlo en `docker-compose.yml`:
```yaml
ports:
  - "8080:5678"  # Cambia 8080 por el puerto que prefieras
```

### n8n no guarda mis cambios
Asegúrate de no borrar el volumen `n8n_data`. Ahí se guardan todas tus automatizaciones.

---

**¿Necesitas ayuda?** Consulta la [documentación oficial](https://docs.n8n.io/) y no dudes en preguntar!
