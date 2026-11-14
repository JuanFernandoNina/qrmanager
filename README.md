# QRManager - Sistema de Gestión y Generación de Códigos QR

Aplicación web monolítica en capas desarrollada para la materia de Taller de Programación.

## Tecnologías
- Python 3.11+
- NiceGUI
- SQLModel & SQLite
- Docker

## Instalación
Clonar el repositorio y entrar en su carpeta:

```bash
git clone https://github.com/JuanFernandoNina/qrmanager.git
cd qrmanager
```

Copiar `.env.example` como `.env` y sustituir `STORAGE_SECRET` por un valor aleatorio, generado con `python -c "import secrets; print(secrets.token_urlsafe(32))"`. No publicar `.env`.

```bash
pip install -r requirements.txt
python -m app.main
```

## Docker
```bash
docker build -t qrmanager-app .
docker run -d --env-file .env -p 8080:8080 --name qrmanager_container qrmanager-app
```

Abrir http://localhost:8080, registrar una cuenta e iniciar sesión para generar códigos QR. Los datos permanecen en el contenedor; para conservarlos al eliminarlo se requiere configurar almacenamiento persistente.

## Arquitectura
- `app/core`: configuración, conexión a la base de datos y hashing de contraseñas.
- `app/models`: entidades User y QRItem.
- `app/repositories`: acceso a los datos.
- `app/services`: autenticación y generación de códigos QR.
- `app/ui`: registro, inicio de sesión y panel de códigos QR.
