# 🎬 Videoclub Java SpringBoot

API REST desarrollada con Spring Boot para la gestión de un videoclub, conectada a una base de datos MySQL. Implementa un CRUD completo siguiendo la arquitectura MVC.

---

## 🛠️ Tecnologías utilizadas

- Java 25
- Spring Boot 4.0.4
- Spring Data JPA
- Hibernate
- MySQL 8.0
- Maven

---

## 📁 Estructura del proyecto
```
src/main/java/com/inditex/videoclub_java_springboot/
├── controller/
│   └── MovieController.java
├── model/
│   └── Movie.java
├── repository/
│   └── MovieRepository.java
├── service/
│   └── MovieService.java
├── CorsConfig.java
└── VideoclubJavaSpringbootApplication.java
```

---

## ⚙️ Configuración de la base de datos

En `src/main/resources/application.properties`:
```properties
spring.application.name=videoclub-java-springboot
spring.datasource.url=jdbc:mysql://localhost:3306/movies_app
spring.datasource.username=root
spring.datasource.password=root
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.MySQLDialect
spring.jpa.properties.hibernate.format-sql=true
```

---

## 🏗️ Arquitectura MVC

### Modelo — `Movie.java`
Entidad JPA que representa una película con los campos: `id`, `titulo`, `director`, `anio`, `genero`, `argumento`, `imagen`, `imageCartel` y `trailer`.

### Repository — `MovieRepository.java`
Interfaz que extiende `JpaRepository<Movie, Integer>` para el acceso a la base de datos.

### Service — `MovieService.java`
Capa de negocio que gestiona la lógica de las operaciones CRUD.

### Controller — `MovieController.java`
Expone los endpoints REST de la API.

---

## 🔗 Endpoints

| Método | Endpoint | Descripción |
|--------|----------|-------------|
| GET | `/movies` | Obtener todas las películas |
| GET | `/movies/{id}` | Obtener una película por id |
| GET | `/movies/ASC` | Obtener películas ordenadas alfabéticamente |
| POST | `/movies` | Crear una nueva película |
| PUT | `/movies/{id}` | Actualizar una película existente |
| DELETE | `/movies/{id}` | Eliminar una película por id |

---

## 📋 Ejemplo de petición POST/PUT
```json
{
    "titulo": "El secreto de sus ojos",
    "director": "Juan José Campanella",
    "año": 2009,
    "genero": "Thriller",
    "argumento": "Un oficial busca resolver un crimen del pasado.",
    "imagen": "src/assets/images/argentina/elSecretoDeSusOjos.jpg",
    "imageCartel": "src/assets/images/argentina/elSecretoDeSusOjosCartel.jpg",
    "trailer": "https://youtu.be/hKa8U-8vsfU"
}
```

---

## 🧪 Testing con Postman

Se han testeado todos los endpoints desde Postman:

- **GET** `/movies` → devuelve array con todas las películas
- **GET** `/movies/{id}` → devuelve la película con el id indicado
- **GET** `/movies/ASC` → devuelve las películas ordenadas por título
- **POST** `/movies` → crea una nueva película y la persiste en la BBDD
- **PUT** `/movies/{id}` → actualiza los campos de una película existente
- **DELETE** `/movies/{id}` → elimina la película de la BBDD

---

## 🌐 Conexión con el Frontend

El backend está conectado con el frontend desarrollado en React, disponible en:
[VideoReactGrupo4](https://github.com/ana-morandeira/VideoReactGrupo4)

La configuración CORS permite las peticiones desde `http://localhost:5173`.


---

## ▶️ Cómo ejecutar el proyecto

1. Clona el repositorio
2. Asegúrate de tener MySQL corriendo con la base de datos `movies_app`
3. Configura las credenciales en `application.properties`
4. Ejecuta el proyecto desde IntelliJ con el botón **Run**
5. La API estará disponible en `http://localhost:8080`
