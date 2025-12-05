# n8n con Redis y PostgreSQL

Este repositorio contiene una configuración lista para usar de n8n,PostgreSQL y Redis utilizando Docker Compose,
permitiendo ejecutar un entorno de automatización robusto, persistente y fácil de desplegar.

## 📋 Requisitos Previos

- Docker y Docker Compose instalados
- NodeJS instalado
- Puertos disponibles: 5678 (n8n), 5432 (PostgreSQL), 6379 (Redis)
- Mínimo 2GB de RAM disponible

## 🚀 Instalación Rápida

### PLUS: Instalación Local de n8n (Con Docker)

Si deseas probar n8n localmente con Docker,ejecuta estos comandos :

```bash
# Instalar n8n globalmente
npm install -g n8n 

# Verificar la instalación
n8n --version

#Empezar a consumirla
docker run -it -p 5678:5678 n8nio/n8n

# Iniciar n8n
n8n 

```
Accede a n8n en: `http://localhost:5678`
---
Primeramente crea una carpeta con el nombre que quieras asignarle y sigue los siguientes pasos

### Clonar el repositorio

```bash
git clone https://github.com/Chologalactico/n8n_DockerCompose.git
cd n8n_DockerCompose
```

### Configurar variables de entorno

Crea un archivo `.env` en la raíz del proyecto:

```env
POSTGRES_USER=n8n
POSTGRES_PASSWORD=tu_password_seguro
POSTGRES_DB=n8n
N8N_ENCRYPTION_KEY= "Pon un valor aletorio mucho mas largo"
N8N_BASIC_AUTH_PASSWORD=
N8N_BASIC_AUTH_USER=
```
⚠️ **Importante sobre N8N_ENCRYPTION_KEY:**

En tal caso de que tengas un error en el levantamiento del contenedor ejecuta 
```bash
./n8n-data/config
```
y te mostrara algo de esta forma 

```bash
{
  "encryptionKey": "tu_llave_vieja_123456789..."
}
```
ya con el encryptionKey copialo en N8N_ENCRYPTION_KEY y vuelve a correrlo 

### Iniciar los servicios

```bash
docker-compose up 
```

### Verificar el estado

```bash
docker-compose ps
```

### Acceder a n8n

Abre tu navegador en: `http://localhost:5678`

## 📁 Estructura del Proyecto

```bash
.
├── docker-compose.yml
├── .env
├── .gitignore
├── README.md
└── data/
    ├── n8n/
    ├── postgres/
    └── redis/
```

## 🔧 Configuración

### Docker Compose

El archivo `docker-compose.yml` define tres servicios:

- **PostgreSQL**: 
- **Redis**: 
- **n8n-worker**: 
- **n8n-main**

### Variables de Entorno Importantes

| Variable | Descripción | Valor por Defecto |
|----------|-------------|-------------------|
| `DB_TYPE` | Tipo de base de datos | `postgresdb` |
| `DB_POSTGRESDB_HOST` | Host de PostgreSQL | `postgres` |
| `QUEUE_BULL_REDIS_HOST` | Host de Redis | `redis` |
| `EXECUTIONS_MODE` | Modo de ejecución | `queue` |

## 🛠️ Comandos Útiles

### Detener los servicios

```bash
docker-compose down
```

### Ver logs

```bash
# Todos los servicios
docker-compose logs -f

# Servicio específico
docker-compose logs -f n8n
```

### Reiniciar un servicio

```bash
docker-compose restart n8n
```
## 🔒 Seguridad

- Cambia todas las contraseñas por defecto en el archivo `.env`
- No subas el archivo `.env` al repositorio
- Considera usar un proxy reverso con SSL/TLS para producción

## 🐛 Solución de Problemas

### n8n no inicia

Verifica los logs:
```bash
docker-compose logs n8n
```

### Error de conexión a PostgreSQL

Asegúrate de que PostgreSQL esté corriendo:
```bash
docker-compose ps postgres
```

### Error de conexión a Redis

Verifica el estado de Redis:
```bash
docker-compose exec redis redis-cli ping
```

## 📚 Recursos Adicionales

- [Documentación oficial de n8n](https://docs.n8n.io/)
- [n8n Community](https://community.n8n.io/)
- [Workflows de ejemplo](https://n8n.io/workflows)

## 🤝 Contribuciones

Las contribuciones son bienvenidas. Por favor:

1. Haz fork del proyecto
2. Crea una rama para tu feature (`git checkout -b feature/AmazingFeature`)
3. Commit tus cambios (`git commit -m 'Add some AmazingFeature'`)
4. Push a la rama (`git push origin feature/AmazingFeature`)
5. Abre un Pull Request

## 📝 Licencia

Este proyecto está bajo la licencia MIT. Ver el archivo `LICENSE` para más detalles.

## ✨ Autor

Tu Nombre - [@Chologalactico](https://github.com/Chologalactico)

---

⭐️ Si este proyecto te fue útil, considera darle una estrella