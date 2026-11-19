<div align="center">

# 🐾 CatCoffe — CrudProyecto_MOFFE

**Plataforma Web Full-Stack para la Gestión de Productos (CRUD), Autenticación de Usuarios y Administración**

[![Python](https://img.shields.io/badge/Python-3.12-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
[![Django](https://img.shields.io/badge/Django-4.2+-092E20?style=for-the-badge&logo=django&logoColor=white)](https://www.djangoproject.com/)
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-Producción-316192?style=for-the-badge&logo=postgresql&logoColor=white)](https://www.postgresql.org/)
[![MySQL](https://img.shields.io/badge/MySQL-Local_XAMPP-005C84?style=for-the-badge&logo=mysql&logoColor=white)](https://www.mysql.com/)
[![Vercel](https://img.shields.io/badge/Vercel-Serverless-000000?style=for-the-badge&logo=vercel&logoColor=white)](https://vercel.com/)
[![License: MIT](https://img.shields.io/badge/Licencia-MIT-yellow.svg?style=for-the-badge)](LICENSE)

[Ver Demo en Vercel](https://cat-coffe-nine.vercel.app) · [Reportar un Bug](https://github.com/michelbarros178-dot/CatCoffe-/issues) · [Solicitar Funcionalidad](https://github.com/michelbarros178-dot/CatCoffe-/issues)

</div>


---

## 📖 Descripción del Proyecto

**CrudProyecto_MOFFE** es una aplicación web desarrollada bajo la arquitectura **MTV (Model-Template-View)** de **Django**. Permite administrar inventarios y catálogos de productos de forma intuitiva, segura y escalable, integrando un entorno híbrido de bases de datos que facilita tanto el desarrollo local con **XAMPP (MySQL)** como el despliegue continuo en la nube mediante **Vercel Serverless Functions** y **PostgreSQL**.

---

## ✨ Características Principales

* 🔐 **Sistema de Autenticación Completo:** Registro, inicio de sesión, cierre de sesión y protección de rutas mediante sesiones de Django.
* 📦 **Gestión Integral de Productos (CRUD):** Creación, visualización, actualización y eliminación de registros en tiempo real.
* 🖼️ **Gestión de Archivos Multimedia:** Soporte para carga y visualización de imágenes asociadas a cada producto.
* 🛡️ **Panel Administrativo:** Interfaz nativa de Django Admin configurada para control total sobre usuarios y modelos.
* 📱 **Interfaz Adaptable (Responsive):** Plantillas HTML5 y CSS3 diseñadas para adaptarse a dispositivos móviles y de escritorio.
* ⚡ **Arquitectura Híbrida & Serverless:** Detección automática del entorno (`DATABASE_URL`) para alternar sin fricciones entre desarrollo local y producción.

---

## 🛠️ Stack Tecnológico

| Categoría | Tecnología | Versión | Propósito |
| :--- | :--- | :--- | :--- |
| **Backend** | Python | `3.12` | Lenguaje de programación principal |
| **Framework** | Django | `4.2+` | Lógica de negocio, ORM, vistas y seguridad |
| **Base de Datos (Prod)** | PostgreSQL | `15+` | Almacenamiento persistente en la nube (`dj-database-url`) |
| **Base de Datos (Dev)** | MySQL / MariaDB | `8.0` | Entorno local mediante XAMPP y `PyMySQL` |
| **Archivos Estáticos** | WhiteNoise | `6.x` | Compresión y entrega eficiente de CSS/JS en producción |
| **Infraestructura** | Vercel | `Serverless` | Alojamiento y ejecución mediante funciones en `/api/index.py` |
| **Control de Versiones** | Git & GitHub | - | Integración y despliegue continuo (CI/CD) |

---

## 📁 Arquitectura del Repositorio

El proyecto utiliza `CrudProyecto_MOFFE` como **Root Directory** en Vercel para aislar el núcleo de Django y su punto de entrada Serverless:

```text
CatCoffe-/                                # Raíz del repositorio en GitHub
├── README.md                             # Documentación principal del proyecto
├── .gitignore                            # Exclusión de entornos virtuales y credenciales
└── CrudProyecto_MOFFE/                   # 📂 Root Directory configurado en Vercel
    ├── api/                              # ⚡ Convención nativa Serverless de Vercel
    │   └── index.py                      # Punto de entrada WSGI para Django
    ├── crud/                             # ⚙️ Configuración central del proyecto Django
    │   ├── __init__.py
    │   ├── asgi.py
    │   ├── settings.py                   # Configuración híbrida (Local / Vercel)
    │   ├── urls.py                       # Enrutamiento global
    │   └── wsgi.py
    ├── productos/                        # 📦 Aplicación principal (Lógica CRUD)
    │   ├── migrations/
    │   ├── static/
    │   ├── templates/
    │   ├── admin.py
    │   ├── apps.py
    │   ├── forms.py
    │   ├── models.py
    │   ├── urls.py
    │   └── views.py
    ├── media/                            # Imágenes subidas por los usuarios
    ├── staticfiles/                      # Estáticos compilados por WhiteNoise
    ├── .python-version                   # Fija Python 3.12 para el entorno de build
    ├── manage.py                         # CLI administrativa de Django
    ├── requirements.txt                  # Dependencias del proyecto
    └── vercel.json                       # Reglas de rewrites hacia /api/index
