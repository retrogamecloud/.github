# 🎮 RetroGameCloud

> Plataforma de juegos retro en la nube con emulación de DOS vía JS-DOS

## 🚀 Sobre el Proyecto

RetroGameCloud es una plataforma moderna para jugar juegos clásicos de DOS directamente en el navegador. Utiliza tecnologías cloud-native, contenedores Docker, y orquestación con Kubernetes para ofrecer una experiencia escalable y de alto rendimiento.

## 🏗️ Arquitectura

```
┌─────────────┐     ┌──────────────┐     ┌─────────────┐
│   Frontend  │────▶│  Kong Gateway│────▶│  Database   │
│  (Nginx)    │     │   (API GW)   │     │  Service    │
└─────────────┘     └──────────────┘     └──────┬──────┘
                                                 │
       ┌─────────────────────────────────────────┘
       │
       ▼
┌─────────────┐
│  PostgreSQL │
│   Database  │
└─────────────┘
```

**Componentes principales:**
- 🌐 **Frontend**: Interfaz web con JS-DOS para emulación de juegos
- 🚪 **Kong Gateway**: API Gateway con CORS, rate limiting y routing
- 🗄️ **Database Service**: Backend unificado Node.js/Express con JWT
- 💾 **PostgreSQL**: Base de datos relacional única
- 📦 **Games CDN**: Servidor Nginx para archivos .jsdos estáticos

## 📚 Repositorios

| Repositorio | Descripción | Tecnologías | CI/CD |
|-------------|-------------|-------------|-------|
| [**database**](https://github.com/retrogamecloud/database) | Backend unificado con autenticación, usuarios, puntuaciones y rankings | Node.js, Express, PostgreSQL, JWT, bcrypt | ✅ |
| [**frontend**](https://github.com/retrogamecloud/frontend) | Interfaz web con JS-DOS y gestión de sesiones | HTML5, JavaScript, JS-DOS | ✅ |
| [**kong**](https://github.com/retrogamecloud/kong) | Configuración de API Gateway con rutas declarativas | Kong 3.3, YAML | ✅ |
| [**infraestructure**](https://github.com/retrogamecloud/infraestructure) | CDN para juegos y recursos estáticos | Nginx, Docker | ✅ |
| [**kubernetes**](https://github.com/retrogamecloud/kubernetes) | Manifiestos para despliegue en Kubernetes | K8s, Helm | 🔄 |

## 🛠️ Stack Tecnológico

**Backend:**
- Node.js 20 Alpine
- Express 4.18
- PostgreSQL 15
- jsonwebtoken 9.0
- bcrypt 5.1

**Frontend:**
- HTML5 / CSS3 / Vanilla JavaScript
- JS-DOS (emulador DOS)
- Nginx Alpine

**Infraestructura:**
- Docker & Docker Compose
- Kong API Gateway 3.3
- Kubernetes (manifiestos YAML)
- GitHub Actions (CI/CD)

**Registros de Imágenes:**
- 📦 Docker Hub: `retrogamehub/*`
- 📦 GitHub Container Registry: `ghcr.io/retrogamecloud/*`

## 🚀 Despliegue Rápido

### Docker Compose (Producción)

```bash
# Clonar repositorio principal
git clone https://github.com/retrogamecloud/database.git
cd database

# Configurar variables de entorno
cp .env.example .env
# Editar JWT_SECRET en .env

# Levantar con imágenes públicas
docker-compose -f docker-compose.prod.yml up -d
```

Accede a: **http://localhost:8000**

### Kubernetes

```bash
# Clonar manifiestos
git clone https://github.com/retrogamecloud/kubernetes.git
cd kubernetes

# Aplicar configuración
kubectl apply -f namespace.yml
kubectl apply -f secrets.yml
kubectl apply -f deployments/
kubectl apply -f services/
kubectl apply -f ingress.yml
```

## 🔐 Seguridad

- ✅ Autenticación JWT con tokens Bearer
- ✅ Contraseñas hasheadas con bcrypt (10 rounds)
- ✅ Tokens con expiración de 24 horas
- ✅ CORS configurado en Kong
- ✅ Rate limiting en API Gateway

## 📊 Características

- 🎮 Emulación de juegos DOS en navegador
- 👤 Sistema de usuarios con registro/login
- 🏆 Tabla de clasificaciones global por juego
- 📈 Estadísticas de usuario
- 💾 Persistencia de puntuaciones
- 🔄 Auto-inicialización de esquema de BD
- 📦 Imágenes Docker optimizadas (Alpine)

## 🔗 Enlaces Útiles

- 📖 [Documentación Database Service](https://github.com/retrogamecloud/database#readme)
- 🐳 [Docker Hub - retrogamehub](https://hub.docker.com/u/retrogamehub)
- 📦 [GitHub Packages](https://github.com/orgs/retrogamecloud/packages)
- 🎮 [JS-DOS Documentation](https://js-dos.com/)

## 📝 Licencia

MIT License © 2025 RetroGameCloud

---

<p align="center">
  <strong>Desarrollado con ❤️ para la comunidad retro gaming</strong>
</p>
