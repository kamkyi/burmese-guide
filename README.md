# Burmese Guide

A Django-based web application with MySQL as the database, running in Docker containers.

## Prerequisites

- Docker
- Docker Compose

## Project Setup

1. Clone the repository:

   ```bash
   git clone <repository-url>
   cd burmese_guide
   ```

2. Build and start the Docker containers:

   ```bash
   docker-compose up --build
   ```

3. Access the application:
   - Open your browser and navigate to `http://0.0.0.0:8000`.

## Services

The project uses the following services:

- **Web**: Django application running on Python 3.10.
- **Database**: MySQL 8.0.

## Environment Variables

The following environment variables are used in the `docker-compose.yml` file:

- `MYSQL_DATABASE`: Name of the MySQL database (default: `burmese_guide`).
- `MYSQL_USER`: MySQL user (default: `user`).
- `MYSQL_PASSWORD`: MySQL user password (default: `password`).
- `MYSQL_ROOT_PASSWORD`: MySQL root password (default: `rootpassword`).

## Database Configuration

The Django application is configured to use MySQL as the database. The database connection settings are defined in `burmese_guide/settings.py`:

```python
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        'NAME': 'burmese_guide',
        'USER': 'user',
        'PASSWORD': 'password',
        'HOST': 'db',
        'PORT': '3306',
    }
}
```

## Wait-for-it Script

The `wait-for-it.sh` script ensures that the Django application waits for the MySQL database to be ready before starting. This script is used in the `docker-compose.yml` file.

## Static Files

Static files are served from the `static/` directory. Update the `STATIC_URL` in `settings.py` if needed.

## Troubleshooting

- If the `web` service fails to connect to the database, ensure the `db` service is running and accessible.
- Rebuild the containers if you make changes to the `Dockerfile` or `requirements.txt`:
  ```bash
  docker-compose build
  ```

## License

This project is licensed under the MIT License. See the `LICENSE` file for details.
