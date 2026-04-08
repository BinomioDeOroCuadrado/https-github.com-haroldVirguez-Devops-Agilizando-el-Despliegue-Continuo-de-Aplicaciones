# Microservicio Lista Negra Global

API REST en Flask para registrar y consultar emails en la lista negra global de la organizacion.

## Endpoints

- `POST /blacklists`: agrega o actualiza un email en lista negra.
- `GET /blacklists/<string:email>`: consulta si un email esta en lista negra.
- `GET /health`: endpoint de salud.

Los endpoints de `blacklists` requieren `Authorization: Bearer <token>`.

## Variables de entorno

Copia `.env.example` a `.env` y ajusta valores:

- `DATABASE_URL`: PostgreSQL para nube; en local puede usarse SQLite.
- `JWT_SECRET_KEY`: secreto HS256 para validar/generar JWT.
- `FLASK_ENV`: `development` o `production`.

## Ejecutar en local

```text
python -m venv .venv
.\.venv\Scripts\pip install -r requirements.txt
.\.venv\Scripts\python -m flask run --host=127.0.0.1 --port=5000
```

Si no tienes PostgreSQL local activo, fuerza SQLite en la sesion:

```text
$env:DATABASE_URL="sqlite:///dev.db"
```

## Generar token JWT para Postman

```text
.\.venv\Scripts\python scripts\issue_jwt_token.py
```

Copia la salida y peguela en `jwt_token` del entorno de Postman.

## Pruebas unitarias

```text
.\.venv\Scripts\pip install -r requirements.txt
.\.venv\Scripts\python -m pytest -q
```

La suite cubre casos de exito, validacion y autorizacion para:

- `POST /blacklists`
- `GET /blacklists/<email>`

## Documentacion Postman

La coleccion y entornos estan en `postman/`.

Guia completa: `postman/README.md`.
