# API de Gestión de Usuarios

Este es un ejemplo de documentación para una API REST usando Markdown. Demuestra las mejores prácticas para documentar APIs en proyectos de desarrollo de software.

## 🚀 Inicio Rápido

### Prerrequisitos

- Node.js >= 14.0.0
- MongoDB >= 4.0
- npm >= 6.0.0

### Instalación

```bash
git clone https://github.com/tu-usuario/api-usuarios.git
cd api-usuarios
npm install
cp .env.example .env
# Configura las variables de entorno
npm start
```

### Configuración

```env
PORT=3000
MONGODB_URI=mongodb://localhost:27017/usuarios
JWT_SECRET=tu_secreto_jwt
NODE_ENV=development
```

## 📡 Endpoints

### Autenticación

#### POST /api/auth/login

Autentica un usuario y devuelve un token JWT.

**Parámetros:**

```json
{
  "email": "usuario@ejemplo.com",
  "password": "contraseña123"
}
```

**Respuesta exitosa (200):**

```json
{
  "success": true,
  "data": {
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...",
    "user": {
      "id": "60d0fe4f5311236168a109ca",
      "name": "Juan Pérez",
      "email": "usuario@ejemplo.com",
      "role": "user"
    }
  }
}
```

**Respuesta de error (401):**

```json
{
  "success": false,
  "error": {
    "message": "Credenciales inválidas",
    "code": "INVALID_CREDENTIALS"
  }
}
```

#### POST /api/auth/register

Registra un nuevo usuario.

**Parámetros:**

```json
{
  "name": "Juan Pérez",
  "email": "usuario@ejemplo.com",
  "password": "contraseña123",
  "confirmPassword": "contraseña123"
}
```

### Usuarios

#### GET /api/users

Obtiene la lista de usuarios con paginación.

**Headers requeridos:**
```
Authorization: Bearer <token>
```

**Query Parameters:**

| Parámetro | Tipo | Descripción | Default |
|-----------|------|-------------|---------|
| `page` | `number` | Número de página | 1 |
| `limit` | `number` | Usuarios por página | 10 |
| `search` | `string` | Búsqueda por nombre o email | - |
| `role` | `string` | Filtrar por rol | - |
| `sort` | `string` | Campo de ordenamiento | name |
| `order` | `string` | Dirección (asc/desc) | asc |

**Ejemplo de petición:**

```bash
curl -X GET "http://localhost:3000/api/users?page=1&limit=5&search=juan" \
  -H "Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9..."
```

**Respuesta exitosa (200):**

```json
{
  "success": true,
  "data": {
    "users": [
      {
        "id": "60d0fe4f5311236168a109ca",
        "name": "Juan Pérez",
        "email": "juan@ejemplo.com",
        "role": "user",
        "active": true,
        "createdAt": "2021-06-21T10:30:00.000Z",
        "updatedAt": "2021-06-21T10:30:00.000Z"
      }
    ],
    "pagination": {
      "page": 1,
      "limit": 5,
      "total": 50,
      "pages": 10,
      "hasNext": true,
      "hasPrev": false
    }
  }
}
```

#### GET /api/users/:id

Obtiene un usuario específico por ID.

**Parámetros de ruta:**
- `id` - ID del usuario (ObjectId de MongoDB)

**Respuesta exitosa (200):**

```json
{
  "success": true,
  "data": {
    "user": {
      "id": "60d0fe4f5311236168a109ca",
      "name": "Juan Pérez",
      "email": "juan@ejemplo.com",
      "role": "user",
      "active": true,
      "profile": {
        "avatar": "https://ejemplo.com/avatar.jpg",
        "bio": "Desarrollador full-stack",
        "phone": "+34 600 123 456"
      },
      "createdAt": "2021-06-21T10:30:00.000Z",
      "updatedAt": "2021-06-21T10:30:00.000Z"
    }
  }
}
```

#### POST /api/users

Crea un nuevo usuario (requiere permisos de admin).

**Parámetros:**

```json
{
  "name": "María García",
  "email": "maria@ejemplo.com",
  "password": "contraseña123",
  "role": "user",
  "profile": {
    "bio": "Diseñadora UX/UI",
    "phone": "+34 600 987 654"
  }
}
```

#### PUT /api/users/:id

Actualiza un usuario existente.

**Parámetros:**

```json
{
  "name": "Juan Pérez Actualizado",
  "profile": {
    "bio": "Senior Full-Stack Developer",
    "phone": "+34 600 111 222"
  }
}
```

#### DELETE /api/users/:id

Elimina un usuario (soft delete).

**Respuesta exitosa (200):**

```json
{
  "success": true,
  "message": "Usuario eliminado correctamente"
}
```

## 📊 Códigos de Estado

| Código | Descripción |
|--------|-------------|
| 200 | Éxito |
| 201 | Creado |
| 400 | Petición incorrecta |
| 401 | No autorizado |
| 403 | Prohibido |
| 404 | No encontrado |
| 422 | Entidad no procesable |
| 500 | Error interno del servidor |

## 🔒 Autenticación y Autorización

### JWT Token

La API usa JWT (JSON Web Tokens) para autenticación. El token debe incluirse en el header `Authorization`:

```
Authorization: Bearer <token>
```

### Roles de Usuario

| Rol | Permisos |
|-----|----------|
| `admin` | Acceso completo a todos los endpoints |
| `moderator` | Puede ver y editar usuarios |
| `user` | Puede ver su propio perfil y editarlo |

## 🚨 Manejo de Errores

### Formato de Error Estándar

```json
{
  "success": false,
  "error": {
    "message": "Descripción del error",
    "code": "ERROR_CODE",
    "details": {
      "field": "Campo que causó el error",
      "value": "Valor inválido"
    }
  }
}
```

### Códigos de Error Comunes

| Código | Descripción |
|--------|-------------|
| `INVALID_CREDENTIALS` | Credenciales de login incorrectas |
| `TOKEN_EXPIRED` | Token JWT expirado |
| `TOKEN_INVALID` | Token JWT inválido |
| `USER_NOT_FOUND` | Usuario no encontrado |
| `EMAIL_ALREADY_EXISTS` | El email ya está registrado |
| `INSUFFICIENT_PERMISSIONS` | Permisos insuficientes |
| `VALIDATION_ERROR` | Error de validación de datos |

## 📝 Modelos de Datos

### Usuario

```javascript
{
  _id: ObjectId,
  name: String (required, min: 2, max: 50),
  email: String (required, unique, valid email),
  password: String (required, min: 6, hashed),
  role: String (enum: ['user', 'moderator', 'admin'], default: 'user'),
  active: Boolean (default: true),
  profile: {
    avatar: String (URL),
    bio: String (max: 500),
    phone: String
  },
  createdAt: Date,
  updatedAt: Date
}
```

## 🧪 Ejemplos de Uso

### JavaScript/Node.js

```javascript
const axios = require('axios');

const API_BASE_URL = 'http://localhost:3000/api';
let authToken = null;

// Login
async function login(email, password) {
  try {
    const response = await axios.post(`${API_BASE_URL}/auth/login`, {
      email,
      password
    });
    
    authToken = response.data.data.token;
    return response.data.data.user;
  } catch (error) {
    console.error('Error en login:', error.response.data);
    throw error;
  }
}

// Obtener usuarios
async function getUsers(page = 1, limit = 10) {
  try {
    const response = await axios.get(`${API_BASE_URL}/users`, {
      params: { page, limit },
      headers: {
        'Authorization': `Bearer ${authToken}`
      }
    });
    
    return response.data.data;
  } catch (error) {
    console.error('Error obteniendo usuarios:', error.response.data);
    throw error;
  }
}

// Uso
(async () => {
  try {
    await login('admin@ejemplo.com', 'admin123');
    const users = await getUsers(1, 5);
    console.log('Usuarios:', users);
  } catch (error) {
    console.error('Error:', error.message);
  }
})();
```

### Python

```python
import requests
import json

class UserAPI:
    def __init__(self, base_url):
        self.base_url = base_url
        self.token = None
    
    def login(self, email, password):
        response = requests.post(f"{self.base_url}/auth/login", json={
            "email": email,
            "password": password
        })
        
        if response.status_code == 200:
            data = response.json()
            self.token = data["data"]["token"]
            return data["data"]["user"]
        else:
            raise Exception(f"Login failed: {response.json()}")
    
    def get_users(self, page=1, limit=10):
        headers = {"Authorization": f"Bearer {self.token}"}
        params = {"page": page, "limit": limit}
        
        response = requests.get(f"{self.base_url}/users", 
                              headers=headers, params=params)
        
        if response.status_code == 200:
            return response.json()["data"]
        else:
            raise Exception(f"Error: {response.json()}")

# Uso
api = UserAPI("http://localhost:3000/api")
user = api.login("admin@ejemplo.com", "admin123")
users = api.get_users(page=1, limit=5)
print(json.dumps(users, indent=2))
```

## 🔧 Testing

### Ejecutar Tests

```bash
# Todos los tests
npm test

# Tests específicos
npm test -- --grep "auth"

# Tests con coverage
npm run test:coverage
```

### Ejemplo de Test

```javascript
describe('POST /api/auth/login', () => {
  it('should login with valid credentials', async () => {
    const res = await request(app)
      .post('/api/auth/login')
      .send({
        email: 'test@ejemplo.com',
        password: 'password123'
      })
      .expect(200);

    expect(res.body.success).toBe(true);
    expect(res.body.data.token).toBeDefined();
    expect(res.body.data.user.email).toBe('test@ejemplo.com');
  });

  it('should reject invalid credentials', async () => {
    const res = await request(app)
      .post('/api/auth/login')
      .send({
        email: 'test@ejemplo.com',
        password: 'wrongpassword'
      })
      .expect(401);

    expect(res.body.success).toBe(false);
    expect(res.body.error.code).toBe('INVALID_CREDENTIALS');
  });
});
```

## 📈 Rate Limiting

La API implementa rate limiting para prevenir abuso:

- **Autenticación**: 5 intentos por IP cada 15 minutos
- **API General**: 100 requests por IP cada 15 minutos
- **Usuarios autenticados**: 1000 requests por usuario cada hora

## 🔄 Versionado

Esta API sigue semantic versioning (SemVer):

- **v1.0.0** - Versión inicial
- **v1.1.0** - Nuevas características sin breaking changes
- **v2.0.0** - Breaking changes

### Changelog

#### v1.1.0 (2024-01-15)
- ✅ Añadido endpoint de búsqueda de usuarios
- ✅ Implementado rate limiting
- 🔧 Mejorado manejo de errores

#### v1.0.0 (2024-01-01)
- 🎉 Versión inicial de la API
- ✅ CRUD de usuarios
- ✅ Autenticación JWT

---

📧 **Soporte**: Para preguntas o problemas, contacta a [soporte@ejemplo.com](mailto:soporte@ejemplo.com)
