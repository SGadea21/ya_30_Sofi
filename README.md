# Fiesta Retro Backend 🎉

Backend API para la aplicación de invitación a fiesta retro 2005-2013.

## 🚀 Tecnologías

- **Java 17**
- **Spring Boot 3.2**
- **Spring Data JPA**
- **PostgreSQL** (Producción)
- **H2** (Desarrollo)
- **Maven**
- **Docker**

## 📋 Características

- ✅ API REST completa
- ✅ Validación de datos
- ✅ Manejo de errores
- ✅ CORS configurado
- ✅ Base de datos con JPA
- ✅ Logging estructurado
- ✅ Health checks
- ✅ Docker ready

## 🛠️ Instalación

### Prerrequisitos
- Java 17+
- Maven 3.6+
- PostgreSQL (para producción)

### Desarrollo Local

1. **Clonar el repositorio**
\`\`\`bash
git clone <tu-repo>
cd fiesta-retro-backend
\`\`\`

2. **Ejecutar con H2 (desarrollo)**
\`\`\`bash
mvn spring-boot:run
\`\`\`

3. **Ejecutar con PostgreSQL**
\`\`\`bash
# Configurar variables de entorno
export DATABASE_URL=jdbc:postgresql://localhost:5432/fiesta_retro
export DATABASE_USERNAME=tu_usuario
export DATABASE_PASSWORD=tu_password

mvn spring-boot:run -Dspring.profiles.active=prod
\`\`\`

### Docker

\`\`\`bash
# Construir imagen
docker build -t fiesta-retro-backend .

# Ejecutar con docker-compose
docker-compose up -d
\`\`\`

## 📚 API Endpoints

### Invitados (Guests)
- `GET /api/guests` - Obtener todos los invitados
- `POST /api/guests` - Crear nuevo invitado
- `GET /api/guests/{id}` - Obtener invitado por ID
- `PUT /api/guests/{id}` - Actualizar invitado
- `DELETE /api/guests/{id}` - Eliminar invitado
- `GET /api/guests/search?q={query}` - Buscar invitados
- `GET /api/guests/with-companions` - Invitados con acompañantes
- `GET /api/guests/total-attendees` - Total de asistentes

### Canciones (Songs)
- `GET /api/songs` - Obtener todas las canciones
- `POST /api/songs` - Agregar nueva canción
- `GET /api/songs/{id}` - Obtener canción por ID
- `PUT /api/songs/{id}` - Actualizar canción
- `DELETE /api/songs/{id}` - Eliminar canción
- `GET /api/songs/search?q={query}` - Buscar canciones
- `GET /api/songs/genre/{genre}` - Canciones por género
- `GET /api/songs/retro` - Canciones retro (2005-2013)
- `GET /api/songs/random?limit={n}` - Canciones aleatorias

### Estadísticas (Stats)
- `GET /api/stats` - Obtener estadísticas generales

### Health Check
- `GET /api/health` - Estado del servicio

## 🌐 Deploy en Railway

### 1. Preparar el proyecto
\`\`\`bash
# Crear cuenta en Railway.app
# Conectar tu repositorio de GitHub
\`\`\`

### 2. Variables de entorno
\`\`\`env
DATABASE_URL=postgresql://usuario:password@host:puerto/database
DATABASE_USERNAME=tu_usuario
DATABASE_PASSWORD=tu_password
SPRING_PROFILES_ACTIVE=prod
\`\`\`

### 3. Deploy automático
Railway detectará automáticamente que es un proyecto Spring Boot y lo deployará.

## 🔧 Configuración de Producción

### Variables de entorno requeridas:
- `DATABASE_URL` - URL de conexión a PostgreSQL
- `DATABASE_USERNAME` - Usuario de la base de datos
- `DATABASE_PASSWORD` - Contraseña de la base de datos
- `PORT` - Puerto del servidor (Railway lo asigna automáticamente)

## 📊 Estructura de Base de Datos

### Tabla: guests
\`\`\`sql
CREATE TABLE guests (
    id BIGSERIAL PRIMARY KEY,
    first_name VARCHAR(100) NOT NULL,
    last_name VARCHAR(100) NOT NULL,
    has_companion BOOLEAN DEFAULT FALSE,
    companion_name VARCHAR(100),
    created_at TIMESTAMP DEFAULT NOW(),
    updated_at TIMESTAMP DEFAULT NOW()
);
\`\`\`

### Tabla: songs
\`\`\`sql
CREATE TABLE songs (
    id BIGSERIAL PRIMARY KEY,
    song_title VARCHAR(200) NOT NULL,
    artist VARCHAR(200) NOT NULL,
    spotify_url VARCHAR(500),
    genre VARCHAR(100),
    suggested_by VARCHAR(200),
    year INTEGER,
    created_at TIMESTAMP DEFAULT NOW()
);
\`\`\`

## 🧪 Testing

\`\`\`bash
# Ejecutar tests
mvn test

# Ejecutar tests con cobertura
mvn test jacoco:report
\`\`\`

## 📝 Ejemplos de Uso

### Crear un invitado
\`\`\`bash
curl -X POST http://localhost:8080/api/guests \
  -H "Content-Type: application/json" \
  -d '{
    "firstName": "Juan",
    "lastName": "Pérez",
    "hasCompanion": true,
    "companionName": "María García"
  }'
\`\`\`

### Agregar una canción
\`\`\`bash
curl -X POST http://localhost:8080/api/songs \
  -H "Content-Type: application/json" \
  -d '{
    "songTitle": "Gasolina",
    "artist": "Daddy Yankee",
    "spotifyUrl": "https://open.spotify.com/track/...",
    "genre": "Reggaeton",
    "year": 2004
  }'
\`\`\`

## 🚀 Próximos Pasos

1. **Deploy del Backend**: Subir a Railway o Render
2. **Configurar Base de Datos**: PostgreSQL en Railway
3. **Conectar Frontend**: Actualizar BACKEND_URL en Vercel
4. **Testing**: Probar todos los endpoints
5. **Monitoreo**: Configurar logs y métricas

## 📞 Soporte

Para problemas o consultas, contacta al equipo de desarrollo.

---

¡Que disfrutes tu fiesta retro! 🎉🎵
