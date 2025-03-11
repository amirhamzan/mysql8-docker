# MySQL Docker Setup

This project uses Docker Compose to run a MySQL 8 database container locally.

## Prerequisites

- Docker installed on your system
- Docker Compose installed (included in Docker Desktop)

## Getting Started

### 1. Start the MySQL Container

Run the following command to start the container:

```sh
docker compose up -d
```

This will start a MySQL container in detached mode.

### 2. Access MySQL Container

To enter the MySQL container shell, use:

```sh
docker exec -it mysql_local_4406 bash
```

To directly access MySQL inside the container:

```sh
docker exec -it mysql_local_4406 mysql -u myuser -p
```

Enter the password (`mypassword`) when prompted.

### 3. Import a SQL File

To import a database dump from the host machine:

```sh
docker cp yourfile.sql mysql_local_4406:/yourfile.sql
docker exec -it mysql_local_4406 mysql -u myuser -p mydatabase < /yourfile.sql
```

### 4. Stop the Container

To stop the container without deleting data:

```sh
docker compose down
```

To remove the container and its data:

```sh
docker compose down -v
```

### 5. Persistent Data Storage

The MySQL database data is stored in a Docker volume to persist even after restarting the container:

```
volumes:
  - mysql_data_jlr_db:/var/lib/mysql
```

### 6. Configuration

Modify `docker-compose.yml` to change database credentials:

```yaml
environment:
  MYSQL_ROOT_PASSWORD: rootpassword
  MYSQL_DATABASE: mydatabase
  MYSQL_USER: myuser
  MYSQL_PASSWORD: mypassword
```

## Troubleshooting

- Check running containers:

  ```sh
  docker ps
  ```

- View logs:

  ```sh
  docker logs mysql_local_4406
  ```

- Restart the container:

  ```sh
  docker restart mysql_local_4406
  ```

---

Enjoy using MySQL with Docker! 🚀

