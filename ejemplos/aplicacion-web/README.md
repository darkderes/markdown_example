# TaskFlow - Aplicación de Gestión de Tareas

Una aplicación web moderna y responsiva para gestión de tareas y proyectos, construida con React, Node.js y MongoDB.

![TaskFlow Screenshot](./docs/images/taskflow-dashboard.png)

[![Deploy Status](https://img.shields.io/badge/deploy-success-brightgreen.svg)](https://taskflow.ejemplo.com)
[![Version](https://img.shields.io/badge/version-1.2.0-blue.svg)](https://github.com/tu-usuario/taskflow/releases)
[![License](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)

## 🌟 Características Principales

### ✅ Gestión de Tareas
- ✏️ Crear, editar y eliminar tareas
- 🏷️ Categorización con etiquetas
- 📅 Fechas límite y recordatorios
- 📊 Estados personalizables (Pendiente, En Progreso, Completado)
- 🔍 Búsqueda y filtrado avanzado

### 👥 Colaboración
- 🤝 Asignación de tareas a usuarios
- 💬 Comentarios en tiempo real
- 📄 Adjuntar archivos y documentos
- 🔔 Notificaciones push
- 📈 Seguimiento de progreso

### 📊 Reportes y Analytics
- 📈 Dashboard con métricas
- 📋 Reportes de productividad
- ⏱️ Seguimiento de tiempo
- 📊 Gráficos interactivos
- 📤 Exportar a PDF/Excel

### 🔧 Características Técnicas
- 📱 Diseño responsivo
- 🌙 Modo oscuro/claro
- 🔄 Sincronización offline
- 🔐 Autenticación segura
- 🌍 Internacionalización (i18n)

## 🖥️ Demo en Vivo

🌐 **Aplicación**: [https://taskflow.ejemplo.com](https://taskflow.ejemplo.com)

**Credenciales de prueba:**
- Usuario: `demo@taskflow.com`
- Contraseña: `demo123`

## 🏗️ Arquitectura

### Frontend (React)
```
src/
├── components/          # Componentes reutilizables
│   ├── common/         # Componentes comunes (Button, Modal, etc.)
│   ├── forms/          # Formularios
│   └── layout/         # Layout y navegación
├── pages/              # Páginas de la aplicación
│   ├── Dashboard/      # Dashboard principal
│   ├── Tasks/          # Gestión de tareas
│   ├── Projects/       # Gestión de proyectos
│   └── Profile/        # Perfil de usuario
├── hooks/              # Custom hooks
├── services/           # API calls y servicios
├── store/              # Estado global (Redux)
├── utils/              # Utilidades
└── styles/             # Estilos globales
```

### Backend (Node.js/Express)
```
server/
├── controllers/        # Controladores de rutas
├── models/            # Modelos de MongoDB
├── middleware/        # Middleware personalizado
├── routes/            # Definición de rutas
├── services/          # Lógica de negocio
├── utils/             # Utilidades del servidor
└── config/            # Configuración
```

## 🚀 Inicio Rápido

### Prerrequisitos

- **Node.js** >= 16.0.0
- **npm** >= 8.0.0
- **MongoDB** >= 5.0
- **Git**

### Instalación Local

1. **Clonar el repositorio**
   ```bash
   git clone https://github.com/tu-usuario/taskflow.git
   cd taskflow
   ```

2. **Instalar dependencias**
   ```bash
   # Instalar dependencias del servidor
   cd server
   npm install

   # Instalar dependencias del cliente
   cd ../client
   npm install
   ```

3. **Configurar variables de entorno**
   ```bash
   # En la carpeta server/
   cp .env.example .env
   
   # Editar .env con tus configuraciones
   nano .env
   ```

   ```env
   # Base de datos
   MONGODB_URI=mongodb://localhost:27017/taskflow
   
   # Autenticación
   JWT_SECRET=tu_jwt_secret_muy_seguro
   JWT_EXPIRE=7d
   
   # Email (opcional)
   EMAIL_HOST=smtp.gmail.com
   EMAIL_PORT=587
   EMAIL_USER=tu-email@gmail.com
   EMAIL_PASS=tu-password
   
   # Configuración del servidor
   NODE_ENV=development
   PORT=5000
   CLIENT_URL=http://localhost:3000
   ```

4. **Inicializar la base de datos**
   ```bash
   cd server
   npm run seed
   ```

5. **Ejecutar la aplicación**
   ```bash
   # Terminal 1: Servidor (desde /server)
   npm run dev
   
   # Terminal 2: Cliente (desde /client)
   npm start
   ```

6. **Abrir en el navegador**
   - Frontend: [http://localhost:3000](http://localhost:3000)
   - API: [http://localhost:5000](http://localhost:5000)

### Usando Docker

```bash
# Clonar y navegar al proyecto
git clone https://github.com/tu-usuario/taskflow.git
cd taskflow

# Construir y ejecutar con Docker Compose
docker-compose up --build

# La aplicación estará disponible en http://localhost:3000
```

## 📱 Capturas de Pantalla

### Dashboard Principal
![Dashboard](./docs/images/dashboard.png)
*Vista general del dashboard con métricas y tareas recientes*

### Lista de Tareas
![Task List](./docs/images/task-list.png)
*Lista de tareas con filtros y búsqueda*

### Crear/Editar Tarea
![Task Form](./docs/images/task-form.png)
*Formulario para crear y editar tareas*

### Vista de Proyecto
![Project View](./docs/images/project-view.png)
*Vista detallada de proyecto con tablero Kanban*

### Modo Oscuro
![Dark Mode](./docs/images/dark-mode.png)
*Interfaz en modo oscuro*

## 🔧 Desarrollo

### Stack Tecnológico

**Frontend:**
- ⚛️ React 18
- 🎨 Material-UI / Styled Components
- 🗂️ Redux Toolkit
- 🛣️ React Router
- 📡 Axios
- 📊 Chart.js
- 🔄 React Query

**Backend:**
- 🟢 Node.js
- ⚡ Express.js
- 🍃 MongoDB + Mongoose
- 🔐 JWT Authentication
- 📧 Nodemailer
- 📁 Multer (file uploads)
- ✅ Joi (validation)

**DevOps:**
- 🐳 Docker
- 🔄 GitHub Actions
- 🌐 Nginx
- ☁️ AWS/Digital Ocean

### Scripts de Desarrollo

```bash
# Cliente (desde /client)
npm start          # Desarrollo
npm run build      # Producción
npm test           # Pruebas
npm run analyze    # Analizar bundle

# Servidor (desde /server)
npm run dev        # Desarrollo con nodemon
npm start          # Producción
npm test           # Pruebas
npm run seed       # Sembrar datos de prueba
npm run migrate    # Ejecutar migraciones
```

### Estructura de la Base de Datos

#### Colección: Users
```javascript
{
  _id: ObjectId,
  name: String,
  email: String (unique),
  password: String (hashed),
  avatar: String,
  role: String (enum: ['user', 'admin']),
  preferences: {
    theme: String (enum: ['light', 'dark']),
    language: String,
    notifications: Boolean
  },
  createdAt: Date,
  updatedAt: Date
}
```

#### Colección: Projects
```javascript
{
  _id: ObjectId,
  name: String,
  description: String,
  owner: ObjectId (ref: User),
  members: [ObjectId] (ref: User),
  status: String (enum: ['active', 'completed', 'archived']),
  color: String,
  dueDate: Date,
  createdAt: Date,
  updatedAt: Date
}
```

#### Colección: Tasks
```javascript
{
  _id: ObjectId,
  title: String,
  description: String,
  project: ObjectId (ref: Project),
  assignedTo: ObjectId (ref: User),
  createdBy: ObjectId (ref: User),
  status: String (enum: ['todo', 'in_progress', 'completed']),
  priority: String (enum: ['low', 'medium', 'high']),
  tags: [String],
  dueDate: Date,
  attachments: [{
    filename: String,
    url: String,
    uploadedAt: Date
  }],
  comments: [{
    user: ObjectId (ref: User),
    content: String,
    createdAt: Date
  }],
  createdAt: Date,
  updatedAt: Date
}
```

### API Endpoints

#### Autenticación
```http
POST   /api/auth/register     # Registro de usuario
POST   /api/auth/login        # Login
POST   /api/auth/logout       # Logout
POST   /api/auth/refresh      # Refresh token
POST   /api/auth/forgot       # Recuperar contraseña
POST   /api/auth/reset/:token # Resetear contraseña
```

#### Usuarios
```http
GET    /api/users           # Obtener usuarios
GET    /api/users/me        # Perfil actual
PUT    /api/users/me        # Actualizar perfil
POST   /api/users/avatar    # Subir avatar
DELETE /api/users/me        # Eliminar cuenta
```

#### Proyectos
```http
GET    /api/projects        # Listar proyectos
POST   /api/projects        # Crear proyecto
GET    /api/projects/:id    # Obtener proyecto
PUT    /api/projects/:id    # Actualizar proyecto
DELETE /api/projects/:id    # Eliminar proyecto
POST   /api/projects/:id/members  # Añadir miembro
```

#### Tareas
```http
GET    /api/tasks           # Listar tareas
POST   /api/tasks           # Crear tarea
GET    /api/tasks/:id       # Obtener tarea
PUT    /api/tasks/:id       # Actualizar tarea
DELETE /api/tasks/:id       # Eliminar tarea
POST   /api/tasks/:id/comments    # Añadir comentario
POST   /api/tasks/:id/attachments # Subir archivo
```

### Testing

#### Frontend
```bash
cd client
npm test                    # Ejecutar pruebas
npm run test:coverage      # Con coverage
npm run test:watch         # Modo watch
```

Ejemplo de prueba:
```javascript
import { render, screen, fireEvent } from '@testing-library/react';
import TaskCard from '../components/TaskCard';

describe('TaskCard', () => {
  const mockTask = {
    id: '1',
    title: 'Test Task',
    status: 'todo',
    priority: 'high'
  };

  it('renders task information correctly', () => {
    render(<TaskCard task={mockTask} />);
    
    expect(screen.getByText('Test Task')).toBeInTheDocument();
    expect(screen.getByText('High Priority')).toBeInTheDocument();
  });

  it('calls onStatusChange when status is updated', () => {
    const mockOnStatusChange = jest.fn();
    render(<TaskCard task={mockTask} onStatusChange={mockOnStatusChange} />);
    
    fireEvent.click(screen.getByText('Mark as Complete'));
    expect(mockOnStatusChange).toHaveBeenCalledWith('1', 'completed');
  });
});
```

#### Backend
```bash
cd server
npm test                    # Ejecutar pruebas
npm run test:watch         # Modo watch
npm run test:coverage      # Con coverage
```

### Despliegue

#### Producción con Docker

1. **Construir imágenes**
   ```bash
   docker build -t taskflow-client ./client
   docker build -t taskflow-server ./server
   ```

2. **Usar Docker Compose**
   ```bash
   docker-compose -f docker-compose.prod.yml up -d
   ```

#### Despliegue Manual

1. **Construir frontend**
   ```bash
   cd client
   npm run build
   ```

2. **Configurar servidor**
   ```bash
   cd server
   npm install --production
   npm start
   ```

3. **Configurar Nginx**
   ```nginx
   server {
       listen 80;
       server_name tu-dominio.com;
       
       location / {
           root /path/to/client/build;
           try_files $uri $uri/ /index.html;
       }
       
       location /api {
           proxy_pass http://localhost:5000;
           proxy_set_header Host $host;
           proxy_set_header X-Real-IP $remote_addr;
       }
   }
   ```

## 🧪 Testing

### Cobertura de Pruebas

| Componente | Cobertura | Estado |
|------------|-----------|--------|
| Frontend Components | 85% | ✅ |
| Backend Controllers | 90% | ✅ |
| API Endpoints | 95% | ✅ |
| Database Models | 80% | ⚠️ |

### Pruebas E2E

```bash
# Instalar Cypress
npm install --save-dev cypress

# Ejecutar pruebas E2E
npm run cypress:open
```

## 📊 Rendimiento

### Métricas de Rendimiento

- **First Contentful Paint**: < 1.5s
- **Largest Contentful Paint**: < 2.5s
- **Time to Interactive**: < 3.0s
- **Cumulative Layout Shift**: < 0.1

### Optimizaciones Implementadas

- 📦 **Code Splitting**: Carga lazy de componentes
- 🗜️ **Compresión**: Gzip en producción
- 🖼️ **Imágenes**: Optimización automática
- 💾 **Caché**: Service Worker para recursos estáticos
- 🔄 **CDN**: Assets servidos desde CDN

## 🌍 Internacionalización

Idiomas soportados:
- 🇪🇸 Español (por defecto)
- 🇺🇸 Inglés
- 🇫🇷 Francés
- 🇩🇪 Alemán

Para añadir un nuevo idioma:

1. Crear archivo de traducción en `client/src/locales/`
2. Añadir importación en `i18n.js`
3. Actualizar selector de idioma

## 🤝 Contribuir

¡Las contribuciones son bienvenidas! Por favor lee nuestra [Guía de Contribución](CONTRIBUTING.md).

### Proceso de Contribución

1. 🍴 Fork el proyecto
2. 🌿 Crea tu rama de característica (`git checkout -b feature/AmazingFeature`)
3. ✅ Commit tus cambios (`git commit -m 'Add some AmazingFeature'`)
4. 📤 Push a la rama (`git push origin feature/AmazingFeature`)
5. 🔀 Abre un Pull Request

### Código de Conducta

Este proyecto adhiere al [Contributor Covenant](https://www.contributor-covenant.org/). Se espera que todos los participantes respeten este código.

## 📄 Licencia

Este proyecto está licenciado bajo la Licencia MIT. Ver [LICENSE](LICENSE) para más detalles.

## 🙏 Agradecimientos

- [React](https://reactjs.org/) - Biblioteca de UI
- [Material-UI](https://mui.com/) - Componentes de UI
- [Express](https://expressjs.com/) - Framework de Node.js
- [MongoDB](https://www.mongodb.com/) - Base de datos
- [Chart.js](https://www.chartjs.org/) - Gráficos
- Todos nuestros [contribuidores](CONTRIBUTORS.md)

## 📞 Soporte y Contacto

- 📧 **Email**: soporte@taskflow.com
- 🐛 **Issues**: [GitHub Issues](https://github.com/tu-usuario/taskflow/issues)
- 💬 **Discord**: [Servidor de la comunidad](https://discord.gg/taskflow)
- 📖 **Documentación**: [Wiki del proyecto](https://github.com/tu-usuario/taskflow/wiki)

## 🗓️ Roadmap

### Versión 1.3.0 (Q2 2024)
- [ ] Integración con calendarios externos
- [ ] API para aplicaciones móviles
- [ ] Plantillas de proyectos
- [ ] Automatización de tareas

### Versión 1.4.0 (Q3 2024)
- [ ] Aplicación móvil (React Native)
- [ ] Integración con Slack/Teams
- [ ] Reportes avanzados con IA
- [ ] Colaboración en tiempo real mejorada

---

Hecho con ❤️ por el equipo de TaskFlow
