# Plantilla de Documentación de API

Esta plantilla proporciona una estructura completa para documentar APIs REST usando Markdown.

## Información General

**Base URL:** `https://api.ejemplo.com/v1`

**Autenticación:** Bearer Token (JWT)

**Formato de respuesta:** JSON

**Versión:** 1.0.0

## Autenticación

Todas las peticiones a la API requieren autenticación mediante Bearer Token.

```http
Authorization: Bearer <token>
```

### Obtener Token

```http
POST /auth/login
Content-Type: application/json

{
  "email": "usuario@ejemplo.com",
  "password": "contraseña"
}
```

**Respuesta:**

```json
{
  "success": true,
  "data": {
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...",
    "expires": "2024-12-31T23:59:59Z"
  }
}
```

## Endpoints

### Usuarios

#### Listar Usuarios

```http
GET /users
```

**Parámetros de consulta:**

| Parámetro | Tipo      | Descripción          | Ejemplo        |
| --------- | --------- | -------------------- | -------------- |
| `page`    | `integer` | Número de página     | `?page=1`      |
| `limit`   | `integer` | Elementos por página | `?limit=10`    |
| `search`  | `string`  | Buscar por nombre    | `?search=juan` |

**Respuesta exitosa (200):**

```json
{
  "success": true,
  "data": {
    "users": [
      {
        "id": 1,
        "name": "Juan Pérez",
        "email": "juan@ejemplo.com",
        "created_at": "2024-01-01T00:00:00Z"
      }
    ],
    "pagination": {
      "page": 1,
      "limit": 10,
      "total": 100,
      "pages": 10
    }
  }
}
```

#### Crear Usuario

```http
POST /users
Content-Type: application/json

{
  "name": "María García",
  "email": "maria@ejemplo.com",
  "password": "contraseña123"
}
```

**Respuesta exitosa (201):**

```json
{
  "success": true,
  "data": {
    "id": 2,
    "name": "María García",
    "email": "maria@ejemplo.com",
    "created_at": "2024-01-01T12:00:00Z"
  }
}
```

## Códigos de Estado

| Código | Descripción                |
| ------ | -------------------------- |
| 200    | Éxito                      |
| 201    | Creado                     |
| 400    | Petición incorrecta        |
| 401    | No autorizado              |
| 403    | Prohibido                  |
| 404    | No encontrado              |
| 422    | Entidad no procesable      |
| 500    | Error interno del servidor |

## Manejo de Errores

Todas las respuestas de error siguen este formato:

```json
{
  "success": false,
  "error": {
    "code": "ERROR_CODE",
    "message": "Descripción del error",
    "details": {
      "field": "campo_con_error",
      "reason": "Razón específica"
    }
  }
}
```

## Rate Limiting

- 1000 peticiones por hora por IP
- 5000 peticiones por hora por usuario autenticado

Los headers de respuesta incluyen información del rate limit:

```http
X-RateLimit-Limit: 1000
X-RateLimit-Remaining: 999
X-RateLimit-Reset: 1609459200
```

## Ejemplos de Código

### JavaScript (Fetch)

```javascript
const API_BASE = "https://api.ejemplo.com/v1";
const token = "tu_token_aqui";

// Obtener usuarios
async function getUsers() {
  const response = await fetch(`${API_BASE}/users`, {
    headers: {
      Authorization: `Bearer ${token}`,
      "Content-Type": "application/json",
    },
  });

  const data = await response.json();
  return data;
}

// Crear usuario
async function createUser(userData) {
  const response = await fetch(`${API_BASE}/users`, {
    method: "POST",
    headers: {
      Authorization: `Bearer ${token}`,
      "Content-Type": "application/json",
    },
    body: JSON.stringify(userData),
  });

  return await response.json();
}
```

### Python (requests)

```python
import requests

API_BASE = 'https://api.ejemplo.com/v1'
TOKEN = 'tu_token_aqui'

headers = {
    'Authorization': f'Bearer {TOKEN}',
    'Content-Type': 'application/json'
}

# Obtener usuarios
def get_users():
    response = requests.get(f'{API_BASE}/users', headers=headers)
    return response.json()

# Crear usuario
def create_user(user_data):
    response = requests.post(
        f'{API_BASE}/users',
        headers=headers,
        json=user_data
    )
    return response.json()
```

## Webhooks

La API puede enviar webhooks para ciertos eventos:

### Configurar Webhook

```http
POST /webhooks
Content-Type: application/json

{
  "url": "https://tu-sitio.com/webhook",
  "events": ["user.created", "user.updated"],
  "secret": "tu_secreto_webhook"
}
```

### Ejemplo de Payload

```json
{
  "event": "user.created",
  "data": {
    "id": 123,
    "name": "Nuevo Usuario",
    "email": "nuevo@ejemplo.com"
  },
  "timestamp": "2024-01-01T12:00:00Z"
}
```

## Changelog

### v1.1.0 (2024-01-15)

- ✅ Agregado endpoint de búsqueda
- ✅ Implementados webhooks
- 🔧 Mejorado rate limiting

### v1.0.0 (2024-01-01)

- 🎉 Versión inicial de la API
- ✅ CRUD básico de usuarios
- ✅ Autenticación JWT
