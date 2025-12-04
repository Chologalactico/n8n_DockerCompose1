# 🚀 Instalación de n8n con PostgreSQL usando Docker Compose

Este repositorio contiene una configuración lista para usar de **n8n** y **PostgreSQL** utilizando **Docker Compose**, permitiendo ejecutar un entorno de automatización robusto, persistente y fácil de desplegar.

---

## 📦 Tecnologías utilizadas

- **Docker** y **Docker Compose**
- **n8n (latest)**
- **PostgreSQL 16**
- **Volúmenes persistentes**
- **Variables de entorno mediante archivo `.env`**

---

## 📂 Estructura del proyecto

n8n-docker-compose/
│── docker-compose.yml
│── .env
│── db-data/ # Datos persistentes de PostgreSQL
│── n8n-data/ # Datos persistentes de n8n (workflows, credenciales, etc.)
└── README.md

---

## ⚙️ Configuración previa

Antes de iniciar, debes crear un archivo `.env` en la raíz del proyecto con el siguiente contenido:

```env
DB_POSTGRES_USER=tu_usuario
DB_POSTGRES_PASSWORD=tu_password
DB_POSTGRES_DB=n8n
