# Reservas Canchas MS Reservas

Reservation microservice for the sports field reservation system.

## Description

This service manages the core business logic of the platform, including:

- sports field management
- reservation creation
- reservation listing
- reservation update and deletion
- reservation ownership validation
- reservation conflict validation

## Tech Stack

- Java 17
- Spring Boot 3
- Spring Data JPA
- PostgreSQL
- Docker

## Project Structure

```text
src/
.mvn/
Dockerfile
pom.xml
mvnw
mvnw.cmd
README.md
````

## Run Locally

```bash id="kwuwo3"
./mvnw spring-boot:run
```

On Windows:

```powershell id="yr7z6l"
.\mvnw.cmd spring-boot:run
```

## Build

```bash id="2scfbm"
./mvnw clean package -DskipTests
```

On Windows:

```powershell id="1tt41h"
.\mvnw.cmd clean package -DskipTests
```

## Docker

This project uses a runtime Dockerfile that expects the jar file to exist in `target/`.

Example workflow:

```powershell id="n8pgf1"
.\mvnw.cmd clean package -DskipTests
docker build -t reservas-canchas-ms-reservas .
```

## Environment Variables

* `SERVER_PORT`
* `SPRING_DATASOURCE_URL`
* `SPRING_DATASOURCE_USERNAME`
* `SPRING_DATASOURCE_PASSWORD`
* `JPA_HIBERNATE_DDL_AUTO`
* `SHOW_SQL`

## Main Endpoints

Examples of available endpoints:

* `/canchas`
* `/canchas/activas`
* `/reservas`
* `/reservas/{id}`

## Notes

* This service receives authentication context through headers propagated by the gateway:

  * `X-User-Id`
  * `X-User-Email`
  * `X-User-Role`
* Reservation ownership is validated using the authenticated user id.
* Reservation conflict rules are enforced by the service.

## Related Repositories

* `reservas-canchas-gateway`
* `reservas-canchas-ms-auth`
* `reservas-canchas-infra`

