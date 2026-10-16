# SQL Server en Docker

Servidor SQL Server (Developer Edition) listo para levantar con Docker Compose.

## Arrancar

```bash
cp .env.example .env      # ajusta la contraseña si quieres
docker compose up -d
```

La primera vez descarga la imagen (~1.5 GB) y crea el volumen de datos.

## Detener / borrar

```bash
docker compose stop       # detiene, conserva datos
docker compose down       # elimina el contenedor, conserva datos (volumen)
docker compose down -v    # elimina TODO, incluida la base de datos
```

## Conectar

| Dato       | Valor        |
| ---------- | ------------ |
| Host       | `localhost`  |
| Puerto     | `1433`       |
| Usuario    | `sa`         |
| Contraseña | la de `.env` |
| Auth       | SQL Login    |
| Trust cert | Sí (`TrustServerCertificate=True`) |

En Azure Data Studio / SSMS: servidor `localhost,1433`, autenticación **SQL Login**,
usuario `sa`, y marca *Trust Server Certificate*.

Cadena de conexión:

```
Server=localhost,1433;User Id=sa;Password=TuPassword123!;TrustServerCertificate=True;Encrypt=False
```

## Ver estado y logs

```bash
docker compose ps
docker compose logs -f
```

El healthcheck pasa a `healthy` cuando el motor termina de arrancar.
