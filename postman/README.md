# Postman — Lista negra global

## Archivos exportables

| Archivo | Uso |
|---------|-----|
| [Blacklist-API.postman_collection.json](Blacklist-API.postman_collection.json) | Colección v2.1 (importar en Postman). Incluye descripciones y ejemplos de respuesta. |
| [Blacklist-API.postman_environment.json](Blacklist-API.postman_environment.json) | Entorno local (`base_url` = `http://127.0.0.1:5000`). |
| [Blacklist-API-AWS.postman_environment.json](Blacklist-API-AWS.postman_environment.json) | Plantilla para despliegue en Elastic Beanstalk (sustituir `base_url`). |

## Importar

1. Postman → **Import** → arrastra los JSON o elige **Upload Files**.
2. Selecciona el entorno **Lista negra — Local** (o AWS) en el selector superior derecho.
3. Rellena **`jwt_token`** en el entorno (ver abajo).

## Token JWT para `jwt_token`

- **Opción A:** [jwt.io](https://jwt.io), algoritmo HS256, mismo secreto que `JWT_SECRET_KEY` de la aplicación, `exp` en el futuro.
- **Opción B:** desde la raíz del repo, con venv y `JWT_SECRET_KEY` definido:

```text
py -3.11 scripts/issue_jwt_token.py
```

Pega el token en la variable de entorno **`jwt_token`**.
