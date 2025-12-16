# 🕹️ RetroGameCloud - Documentación general

[![Hosted on AWS EKS](https://img.shields.io/badge/Hosted%20on-AWS%20EKS-FF9900?logo=amazoneks&logoColor=white)](https://aws.amazon.com/eks/)
[![Node.js](https://img.shields.io/badge/Node.js-20.19.5-339933?logo=node.js&logoColor=white)](https://nodejs.org/)
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-15-4169E1?logo=postgresql&logoColor=white)](https://www.postgresql.org/)
[![Kubernetes](https://img.shields.io/badge/Kubernetes-1.34-326CE5?logo=kubernetes&logoColor=white)](https://kubernetes.io/)
[![Terraform](https://img.shields.io/badge/Terraform-IaC-7B42BC?logo=terraform&logoColor=white)](https://www.terraform.io/)
[![ArgoCD](https://img.shields.io/badge/ArgoCD-GitOps-EF7B4D?logo=argo&logoColor=white)](https://argo-cd.readthedocs.io/)
[![Kong](https://img.shields.io/badge/Kong-API%20Gateway-003459?logo=kong&logoColor=white)](https://konghq.com/)
[![Docker](https://img.shields.io/badge/Docker-Containers-2496ED?logo=docker&logoColor=white)](https://www.docker.com/)
[![GitHub Actions](https://img.shields.io/badge/GitHub%20Actions-CI%2FCD-2088FF?logo=githubactions&logoColor=white)](https://github.com/features/actions)
[![Grafana](https://img.shields.io/badge/Grafana-Monitoring-F46800?logo=grafana&logoColor=white)](https://grafana.com/)
[![Prometheus](https://img.shields.io/badge/Prometheus-Metrics-E6522C?logo=prometheus&logoColor=white)](https://prometheus.io/)
[![SonarCloud](https://img.shields.io/badge/SonarCloud-Quality-F3702A?logo=sonarcloud&logoColor=white)](https://sonarcloud.io/)


**RetroGameCloud** es una plataforma cloud-native completa para jugar juegos clásicos de DOS directamente en tu navegador. El proyecto combina tecnologías modernas de desarrollo web, infraestructura como código, y orquestación de contenedores.

La aplicación está desplegada sobre **Kubernetes en AWS EKS**, gestionada íntegramente mediante **Terraform** para la infraestructura y **ArgoCD** para el despliegue continuo. Siguiendo metodologías **GitOps** y **Gitflow**, cada cambio en los repositorios desencadena pipelines automatizados de CI/CD con **GitHub Actions**, incluyendo testing, análisis de calidad (SonarCloud), escaneo de seguridad (Trivy), y despliegue automático a través de sincronización declarativa.

El stack de la aplicación incluye un **backend API REST** con Node.js y PostgreSQL, un **frontend** con emulador DOS.js integrado, junto a un sistema completo de **monitoreo** con Grafana y Prometheus. Al ser un proyecto educativo, el uso de los recursos equilibra los costes y la funcionalidad, diseñando y adaptando una arquitectura que no sea demasiado costosa pero garantizando unos mínimos.

[![Consulta nuestra documentación en Mintlify.com](https://img.shields.io/badge/Consulta%20nuestra%20documentaci%C3%B3n%20en-Mintlify.com-4C9CF0?logo=readthedocs&logoColor=white)](https://retrogamecloud.mintlify.app/)
[![Consulta nuestra presentación en YouTube.com](https://img.shields.io/badge/Consulta%20nuestra%20presentaci%C3%B3n%20en-YouTube.com-FF0000?logo=youtube&logoColor=white)](https://youtu.be/hCEmI6w48bg)
[Consulta nuestras diapositivas en Slides.com](https://slides.com/retrogamecloud/retrogamecloud)

---

## Tabla de Contenidos

- [¿Qué es RetroGameCloud?](#qué-es-retrogamecloud)
- [Arquitectura General](#arquitectura-general)
- [Stack Tecnológico](#stack-tecnológico)
- [Repositorios del Proyecto](#repositorios-del-proyecto)
- [Guía Rápida de Instalación](#guía-rápida-de-instalación)
- [Despliegue en AWS EKS](#despliegue-en-aws-eks)
- [Documentación Detallada](#documentación-detallada)
- [Estrategia CI/CD](#estrategia-cicd)
- [Troubleshooting General](#troubleshooting-general)
- [Seguridad](#seguridad)
- [Monitoreo y Observabilidad](#monitoreo-y-observabilidad)
- [Estimación de Costos AWS](#estimación-de-costos-aws)
- [Enlaces Útiles](#enlaces-útiles)
- [Equipo](#equipo)

---

## 📚 Índice de README del Proyecto

- 📘 [backend](https://github.com/retrogamecloud/backend/blob/main/README.md)
  - 📋 [.github](https://github.com/retrogamecloud/backend/blob/main/.github/README-WF.md)
  - 📝 [tests](https://github.com/retrogamecloud/backend/blob/main/tests/README.md)
- 📗 [frontend](https://github.com/retrogamecloud/frontend/blob/main/README.md)
  - 📋 [.github](https://github.com/retrogamecloud/frontend/blob/main/.github/README-WF.md)
- 📙 [kong](https://github.com/retrogamecloud/kong/blob/main/README.md)
- 📕 [kubernetes](https://github.com/retrogamecloud/kubernetes/blob/main/README.md)
  - 📋 [.github](https://github.com/retrogamecloud/kubernetes/blob/main/.github/README-WF.md)
- 📔 [infrastructure](https://github.com/retrogamecloud/infrastructure/blob/main/README.md)
  - 📋 [.github](https://github.com/retrogamecloud/infrastructure/blob/main/.github/README-WF.md)
  - 📝 [argocd](https://github.com/retrogamecloud/infrastructure/blob/main/argocd/README.md)
  - terraform/
    - 📝 [bootstrap](https://github.com/retrogamecloud/infrastructure/blob/main/terraform/bootstrap/README.md)
    - 📝 [eks](https://github.com/retrogamecloud/infrastructure/blob/main/terraform/eks/README.md)
    - 📝 [github](https://github.com/retrogamecloud/infrastructure/blob/main/terraform/github/README.md)
- 📓 [docs](https://github.com/retrogamecloud/docs/blob/main/README.md)

---

## ¿Qué es RetroGameCloud?

RetroGameCloud consolida todo lo que necesitas para:

✅ **Jugar juegos retro** - Emulador DOS.js integrado en el navegador  
✅ **Gestionar usuarios** - Autenticación JWT + perfiles personalizados  
✅ **Registrar puntuaciones** - Sistema de scores y rankings  
✅ **Escalar en la nube** - Desplegado en Kubernetes con GitOps (ArgoCD)  
✅ **Monitorizar** - Observabilidad con Grafana y Prometheus  

### Características Principales

| Característica | Descripción |
|---|---|
| **Emulación** | DOS.js - Juegos clásicos en HTML5 |
| **Autenticación** | JWT + bcrypt, sin gestión de sesiones manual |
| **Puntuaciones** | Sistema centralizado con historiales |
| **Rankings** | Cálculos agregados por juego y globales |
| **Escalabilidad** | Kubernetes 1.34 + Auto-scaling con Karpenter |
| **Seguridad** | SSL/TLS, CORS configurado, rate limiting |
| **CI/CD** | GitHub Actions + ArgoCD GitOps |
| **Monitoreo** | Grafana dashboards + Prometheus métricas |

---

## Arquitectura General

[![Diagrama RetroGameCloud](https://github.com/retrogamecloud/.github/blob/main/Diagrama%20-%20RetroGameCloud.png?raw=true)](https://drive.google.com/file/d/1etPAeG28t6YKcKOv5wlC8F5EzALjWfse/view?usp=sharing)

**Stack de Infraestructura:**
- **Cloud:** AWS (eu-west-1)
- **Orquestación:** Kubernetes 1.34 (EKS)
- **GitOps:** ArgoCD (sincronización automática)
- **Ingress:** Kong API Gateway
- **Monitoreo:** Grafana + Prometheus
- **DNS:** Route53 + ACM Certificate

---

## Stack Tecnológico

### Backend
- **Runtime:** Node.js 20.19.5 (LTS)
- **Framework:** Express.js 4.18.2
- **BD:** PostgreSQL 15-alpine
- **Auth:** JWT (jsonwebtoken 9.0.2) + bcrypt 5.1.1
- **Testing:** Jest 29.7.0 + Supertest 6.3.3
- **Quality:** ESLint 9.39.1 + SonarQube
- **Env Management:** Variables de entorno

### Frontend
- **Runtime:** Node.js 20 (LTS)
- **Framework:** Express.js 5.1.0
- **UI:** HTML5 + CSS3 (tema retro)
- **Emulador:** jsdos.js (DOS.js)
- **Testing:** Jest 29.7.0 + Supertest
- **Client:** Fetch API + localStorage

### Infrastructure
- **IaC:** Terraform (~> 20.0 EKS, ~> 5.0 VPC)
- **Container Registry:** GitHub Container Registry (GHCR)
- **CI/CD:** GitHub Actions
- **GitOps:** ArgoCD (v2.10+)
- **API Gateway:** Kong 3.3
- **Monitoring:** Grafana + Prometheus
- **CDN:** Nginx

### Kubernetes
- **Versión:** 1.34 (EKS)
- **Networking:** VPC privada (10.0.0.0/16), 3 AZs
- **Node Scaling:** Karpenter (auto-scaling)
- **Secret Management:** Kubernetes Secrets (considerar Sealed Secrets)
- **Ingress:** Kong
- **Storage:** EBS volumes para PostgreSQL

---

## Repositorios del Proyecto

### 1️⃣ Backend (`/backend`)
Servicio unificado que consolida autenticación, usuarios, puntuaciones, rankings y catálogo de juegos.

- **Tecnología:** Node.js 20 + Express 4.18 + PostgreSQL 15
- **Puertos:** 3000
- **Endpoints:** `/api/auth/*`, `/api/scores/*`, `/api/rankings/*`, `/api/users/*`, `/api/games/*`
- **Testing:** Jest (cobertura 70%) con validaciones SonarCloud
- **📖 Documentación completa:** [`Backend README`](https://github.com/retrogamecloud/backend/blob/main/README.md)
- **📋 Workflows CI/CD:** [`Documentación de Workflows`](https://github.com/retrogamecloud/backend/blob/main/.github/README-WF.md)

```bash
# Inicio rápido local
cd backend
npm install
docker-compose up -d
npm start
```

---

### 2️⃣ Frontend (`/frontend`)
Aplicación web Express que sirve HTML/CSS/JS con emulador DOS.js integrado.

- **Tecnología:** Express 5.1 + jsdos.js
- **Puertos:** 8081 (desarrollo) / 8080 (producción)
- **Rutas:** Login, juegos, perfil, rankings
- **Testing:** Jest con validaciones SonarCloud
- **📖 Documentación completa:** [`Frontend README`](https://github.com/retrogamecloud/frontend/blob/main/README.md)
- **📋 Workflows CI/CD:** [`Documentación de Workflows`](https://github.com/retrogamecloud/frontend/blob/main/.github/README-WF.md)

```bash
# Inicio rápido local
cd frontend
npm install
npm start
```

---

### 3️⃣ Kong Gateway (`/kong`)
API Gateway declarativo que enruta tráfico hacia Backend, Frontend y CDN.

- **Tecnología:** Kong 3.3 + YAML config
- **Puertos:** 8000 (proxy), 8001 (admin)
- **Rutas configuradas:**
  - `/api/*` → Backend (3000)
  - `/` → Frontend (8081)
  - `/cdn/*` → Games CDN (8086)
- **Plugins:** CORS, rate-limiting, authentication
- **📖 Documentación completa:** [`Kong README`](https://github.com/retrogamecloud/kong/blob/main/README.md)

---

### 4️⃣ Kubernetes (`/kubernetes`)
Manifiestos YAML para desplegar todos los servicios en Kubernetes.

- **Estructura:** Namespace `retrogame`, Deployments, Services, Secrets, ConfigMaps
- **ArgoCD:** Sincronización automática con GitOps
- **Componentes:**
  - PostgreSQL (StatefulSet)
  - Backend (Deployment x2 replicas)
  - Frontend (Deployment)
  - Kong Gateway (Deployment)
  - Games CDN (Deployment)
- **📖 Documentación completa:** [`Kubernetes README`](https://github.com/retrogamecloud/kubernetes/blob/main/README.md)
- **📋 Workflows CI/CD:** [`Documentación de Workflows`](https://github.com/retrogamecloud/kubernetes/blob/main/.github/README-WF.md)

---

### 5️⃣ Infrastructure (`/infrastructure`)
Terraform + ArgoCD + Monitoring para crear y gestionar el cluster EKS.

- **Terraform:** Crea VPC, EKS, RDS (opcional), ALB, Route53, ACM
- **AWS Region:** eu-west-1 (Irlanda)
- **EKS Version:** 1.34
- **Monitoreo:** Grafana dashboards + Prometheus scraping
- **Costos estimados:** ~$200-300/mes (dev), ~$500-800/mes (prod)
- **📖 Documentación completa:** [`Infrastructure README`](https://github.com/retrogamecloud/infrastructure/blob/main/README.md)
- **📋 Workflows CI/CD:** [`Documentación de Workflows`](https://github.com/retrogamecloud/infrastructure/blob/main/.github/README-WF.md)

---

### 6️⃣ Documentación (`/docs`)
Documentación con Mintlify (repositorio separado).

- **Tecnología:** Mintlify (MDX)
- **Contenido:** Arquitectura, API reference, guías de desarrollo, operaciones

---

## Guía Rápida de Instalación

### Requisitos Previos

- Git
- Docker & Docker Compose
- Node.js 20+ (para desarrollo local sin Docker)
- kubectl (para operaciones K8s)
- Terraform 1.6+ (para infrastructure)

### Instalación Local (Docker Compose)

```bash
# 1. Clonar todos los repositorios
git clone https://github.com/retrogamecloud/.github.git
cd .github

# 2. Inicializar submódulos (si están configurados)
git submodule update --init --recursive

# 3. Levantar stack completo
docker-compose up -d

# 4. Verificar servicios
docker-compose ps

# 5. Acceder a la aplicación
# Frontend: http://localhost:8081
# API Gateway: http://localhost:8000
# Backend directo: http://localhost:3000
```

**Variables de entorno necesarias:**

```bash
# backend/.env
JWT_SECRET=tu_clave_muy_segura_cambiar_en_produccion
NODE_ENV=development
DATABASE_URL=postgresql://gamecloud:gamecloud@postgres-db:5432/retrogamecloud

# frontend/.env
API_GATEWAY_URL=http://localhost:8000
CDN_BASE_URL=http://localhost:8086
```

👉 Ver documentación específica de cada repo para más detalles.

---

## Despliegue en AWS EKS

### Requisitos AWS

- Cuenta AWS con permisos AdministratorAccess
- AWS CLI v2 configurado
- Credenciales de AWS en variables de entorno
- Dominio registrado (retrogamehub.games)
- GitHub Personal Access Token (PAT) con scope `read:packages`

### Paso 1: Crear Infraestructura con Terraform

```bash
cd infrastructure/terraform/bootstrap

# Crear S3 backend para state (primera vez)
terraform init
terraform plan -var="environment=dev"
terraform apply -var="environment=dev"

# Guardar el backend S3 output
cd ../eks

# Usar backend S3 creado
terraform init -backend-config="bucket=retrogame-terraform-state-..."

# Crear EKS cluster
terraform plan -var-file=dev.tfvars
terraform apply -var-file=dev.tfvars

# Tomar nota de outputs (kubeconfig, ALB DNS)
```

### Paso 2: Configurar kubectl

```bash
# Actualizar kubeconfig
aws eks update-kubeconfig \
  --region eu-west-1 \
  --name retrogame

# Verificar conexión
kubectl get nodes
```

### Paso 3: Desplegar con ArgoCD

```bash
# Verificar ArgoCD está instalado (Terraform lo hace automáticamente)
kubectl get ns | grep argocd

# Acceder a ArgoCD
kubectl port-forward -n argocd svc/argocd-server 8080:443

# Usuario: admin
# Contraseña: (en secret)
# URL: https://localhost:8080
```

### Paso 4: Sincronizar Aplicación

```bash
# ArgoCD sincroniza automáticamente
# O forzar sincronización:
argocd app sync argocd-config
```

### Verificar Despliegue

```bash
# Ver pods corriendo
kubectl get pods -n retrogame

# Ver servicios
kubectl get svc -n retrogame

# Logs del backend
kubectl logs -n retrogame -l app=backend -f

# Acceder a la aplicación
# https://retrogamehub.games
```

👉 Ver [`Infrastructure README`](https://github.com/retrogamecloud/infrastructure/blob/main/README.md) para detalles completos.

---

## Documentación Detallada

| Documentación | Descripción | Ubicación |
|---|---|---|
| **Backend** | API, autenticación, endpoints, testing | [`README`](https://github.com/retrogamecloud/backend/blob/main/README.md) / [`Workflows`](https://github.com/retrogamecloud/backend/blob/main/.github/README-WF.md) |
| **Frontend** | Interfaz, emulador, rutas, componentes | [`README`](https://github.com/retrogamecloud/frontend/blob/main/README.md) / [`Workflows`](https://github.com/retrogamecloud/frontend/blob/main/.github/README-WF.md) |
| **Kong** | Gateway, rutas, plugins, configuración | [`README`](https://github.com/retrogamecloud/kong/blob/main/README.md) |
| **Kubernetes** | Manifiestos, ArgoCD, despliegue, rollback | [`README`](https://github.com/retrogamecloud/kubernetes/blob/main/README.md) / [`Workflows`](https://github.com/retrogamecloud/kubernetes/blob/main/.github/README-WF.md) |
| **Infrastructure** | Terraform, AWS, monitoreo, costos | [`README`](https://github.com/retrogamecloud/infrastructure/blob/main/README.md) / [`Workflows`](https://github.com/retrogamecloud/infrastructure/blob/main/.github/README-WF.md) |
| **Profesional** | API docs, arquitectura, guías DevOps | [`https://retrogamecloud.mintlify.app/`](https://retrogamecloud.mintlify.app/) |
| **Testing** | Estrategia de testing en cada repo | `/{repo}/tests/README.md` |
| **Secretos** | Estrategia de manejo de secretos | [`SECRETS-STRATEGY`](https://github.com/retrogamecloud/docs/blob/main/SECRETS-STRATEGY.md) |

---

## Estrategia CI/CD

Cada repositorio del proyecto implementa validaciones automáticas mediante GitHub Actions. A continuación se describe qué se valida en cada uno:

### Backend & Frontend

**Workflows:** `cicd.yml`, `rollback-*.yml`, `dependabot.yml`

✅ **Validaciones automáticas:**
- **Testing:** Jest con cobertura mínima 70%
- **Linting:** ESLint para calidad de código
- **Seguridad de imágenes:** Trivy escanea vulnerabilidades en Docker
- **Análisis estático:** SonarCloud detecta code smells y bugs
- **Build:** Construcción de imágenes Docker y push a GHCR
- **Despliegue automático:** Actualización de manifiestos Kubernetes vía GitOps
- **Rollback:** Workflow manual para revertir despliegues si es necesario
- **Dependencias:** Dependabot mantiene librerías actualizadas

📋 Ver documentación completa en [`README-WF.md`](https://github.com/retrogamecloud/backend/blob/main/.github/README-WF.md) de cada repositorio.

### Kubernetes

**Workflows:** `ci.yml`, `delete-old-branchs.yml`, `dependabot.yml`

✅ **Validaciones automáticas:**
- **Validación YAML:** Kube-score y kubeval verifican sintaxis de manifiestos
- **Seguridad:** Network policies, RBAC, Pod Security Standards
- **Escaneo de vulnerabilidades:** Trivy valida manifiestos
- **Análisis estático:** SonarCloud detecta problemas de configuración
- **Limpieza:** Eliminación automática de ramas antiguas (> 30 días)
- **Dependabot:** Actualizaciones de dependencias

📋 Ver documentación completa en [`README-WF.md`](https://github.com/retrogamecloud/kubernetes/blob/main/.github/README-WF.md).

### Infrastructure

**Workflows:** `validate-and-scan.yml`, `dependabot.yml`

✅ **Validaciones automáticas:**
- **Terraform:** `terraform fmt`, `terraform init`, `terraform validate`
- **Seguridad:** Trivy escanea configuración de Terraform
- **Análisis estático:** SonarCloud para IaC
- **ArgoCD:** Validación de manifiestos GitOps
- **Notificaciones:** Slack alertas para fallos críticos

📋 Ver documentación completa en [`README-WF.md`](https://github.com/retrogamecloud/infrastructure/blob/main/.github/README-WF.md).

### Configuración de Secrets

Todos los workflows utilizan secretos almacenados en **AWS Secrets Manager**, NO en los repositorios públicos:

| Secret | Uso | Almacenamiento |
|---|---|---|
| `GHCR_TOKEN` | Push a GitHub Container Registry | AWS Secrets Manager |
| `SONARCLOUD_TOKEN` | Análisis de código SonarCloud | AWS Secrets Manager |
| `SLACK_WEBHOOK` | Notificaciones de fallos | AWS Secrets Manager |
| `KUBERNETES_CONFIG` | Acceso a cluster EKS (si aplica) | AWS Secrets Manager |

👉 Documentación detallada en [`SECRETS-STRATEGY.md`](https://github.com/retrogamecloud/docs/blob/main/SECRETS-STRATEGY.md).

---

## Troubleshooting General

### Los servicios no se levantan en Docker Compose

```bash
# Verificar logs
docker-compose logs -f

# Verificar puertos disponibles
netstat -ano | findstr :3000
netstat -ano | findstr :8081

# Limpiar y reiniciar
docker-compose down -v
docker-compose up -d
```

### Error: ECONNREFUSED en Backend

```bash
# PostgreSQL no está corriendo
docker-compose logs postgres-db

# Verificar health check
docker-compose ps postgres-db

# Reiniciar BD
docker-compose restart postgres-db
```

### Error: JWT_SECRET no configurado

```bash
# Generar JWT_SECRET fuerte
openssl rand -base64 32

# Configurar en .env
echo "JWT_SECRET=$(openssl rand -base64 32)" >> backend/.env
```

### Kubernetes: Pods no arrancan

```bash
# Ver estado de pods
kubectl get pods -n retrogame
kubectl describe pod -n retrogame <pod-name>

# Ver logs
kubectl logs -n retrogame <pod-name>

# Verificar secrets
kubectl get secrets -n retrogame
kubectl describe secret postgres-secret -n retrogame
```

### ArgoCD: Aplicación no sincroniza

```bash
# Ver estado de ArgoCD
argocd app get argocd-config

# Forzar resincronización
argocd app sync argocd-config --force

# Ver logs de ArgoCD
kubectl logs -n argocd -l app.kubernetes.io/name=argocd-controller-manager -f
```

👉 Para troubleshooting específico, ver documentación de cada servicio.

---

### Proceso de Cambios

1. Comunica los cambios propuestos al equipo
2. Crea una rama: `git checkout -b feature/tu-feature`
3. Realiza cambios y tests: `npm test`
4. Push a la rama: `git push origin feature/tu-feature`
5. Abre un Pull Request

**Estándares:**
- ✅ Tests con cobertura mínima 70%
- ✅ Linting: `npm run lint:fix`
- ✅ Commits semánticos (feat:, fix:, docs:, etc.)
- ✅ Documentación actualizada

---

## Seguridad

### Gestión de Secretos

RetroGameCloud maneja múltiples secretos en diferentes niveles. **Nunca commitees secretos a Git.**

**Estrategia recomendada:**
- Desarrollo: Variables de entorno en `.env.local` (ignorado en Git)
- Staging/Prod: AWS Secrets Manager
- Kubernetes: Sealed Secrets o External Secrets Operator

👉 Ver [`SECRETS-STRATEGY.md`](https://github.com/retrogamecloud/docs/blob/main/SECRETS-STRATEGY.md) para estrategia detallada.

### SSL/TLS

- Certificado: AWS ACM (auto-renovable)
- Dominio: retrogamehub.games
- Redirects: HTTP → HTTPS automático en ALB

### CORS & Rate Limiting

- Configurados en Kong Gateway
- CORS Origin: https://retrogamehub.games
- Rate Limit: 100 requests/minuto por IP

---

## Monitoreo y Observabilidad

### Grafana Dashboards

- **URL:** https://retrogamehub.games/grafana/
- **Dashboards:** Application, Infrastructure, PostgreSQL, Kong
- **Métricas:** Prometheus scraping cada 15 segundos

### Prometheus

- **URL:** https://retrogamehub.games/prometheus/
- **Retention:** 30 días
- **Alertas:** Configuradas en AlertManager

### Logs

- **Backend:** Stdout a CloudWatch (opcional)
- **Kubernetes:** Fluent Bit → CloudWatch
- **Acceso:** AWS CloudWatch Logs

---

## Estimación de Costos AWS

| Servicio | Descripción | Costo/mes (dev) | Costo/mes (prod) |
|---|---|---|---|
| EKS | 1 cluster | $73 | $73 |
| EC2 | On-demand (2-4 nodes) | $40-80 | $200-400 |
| RDS | PostgreSQL (db.t3.micro) | $30 | $100 |
| ALB | 1 load balancer | $16 | $16 |
| Route53 | DNS + queries | $2 | $2 |
| Data Transfer | Egress (estimado) | $5 | $10 |
| **Total** | | **$166-206** | **$401-601** |

> Nota: Precios estimados para eu-west-1, pueden variar. Usar AWS Calculator para precisión.

---

## Enlaces Útiles

- **Aplicación:** https://retrogamehub.games
- **Documentación:** https://retrogamecloud.mintlify.app/
- **GitHub Org:** https://github.com/retrogamecloud

---

## Equipo

### Evaristo García Zambrana
[![GitHub](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/EvaristoGZ)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/evaristogz/)

### José María Palenzuela
[![GitHub](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/jpalenz77)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/josemariapalenzuelaplaza/)

### Miguel Ángel Narvaiz
[![GitHub](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/naesman1)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/miguel-narvaiz/)
