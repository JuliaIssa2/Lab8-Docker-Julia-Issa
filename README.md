
# Lab 8 – Docker and Containers

**Student:** Julia Issa  
**AUB Username:** jai10  
**Course:** EECE 439 – Software Tools  
**Academic Year:** 2026–2027  
**Submission:** Individual

## Project Overview

This lab demonstrates how to containerize Python Flask applications using Docker, build and run Docker images, and manage containers using Docker CLI commands.

The project contains two activities.

## Activity 1 – Flask Hello World

A simple Flask application was created and containerized using Docker. The application listens on port 5000.

### Build and run

```powershell
cd activity1
docker build -t flask_docker .
docker run -d --name lab8-hello -p 5000:5000 flask_docker
```

Open `http://localhost:5000`.

### Docker commands demonstrated

- `docker ps -a` – List all containers.
- `docker stop lab8-hello` – Stop the running container.
- `docker logs lab8-hello` – Display container logs.

## Activity 2 – Two Docker Versions

The Flask and SQLite API from Lab 5 was reused.

### Version 1 – Original API

- Docker image: `jai10/lab8-julia_issa:0.0.1.RELEASE`
- Port: `5000`
- Test endpoint: `GET /api/users`

```powershell
cd activity2/version1
docker build -t jai10/lab8-julia_issa:0.0.1.RELEASE .
docker run -d --name lab8-version1 -p 5000:5000 jai10/lab8-julia_issa:0.0.1.RELEASE
```

Endpoint: `http://localhost:5000/api/users`

### Version 2 – Updated API

- Docker image: `jai10/lab8-julia_issa:0.0.2.RELEASE`
- Port: `3000`
- New endpoint: `GET /get_users`

```powershell
cd activity2/version2
docker build -t jai10/lab8-julia_issa:0.0.2.RELEASE .
docker run -d --name lab8-version2 -p 3000:3000 jai10/lab8-julia_issa:0.0.2.RELEASE
```

Endpoint: `http://localhost:3000/get_users`

The new endpoint retrieves user names from the SQLite database and returns them as JSON.

Both versions can run simultaneously on ports 5000 and 3000. Activity 1 must be stopped first because it also uses port 5000.

## Documentation

See `Julia_Issa_Lab8_Report.docx` for screenshots, Docker command explanations, image verification, and API testing results.

## Notes

The SQLite database contains test records with sanitized contact information. No real credentials are required.

## Conclusion

Both Docker image versions were built and tested successfully. The second version extends the original Flask API with a new endpoint while preserving existing functionality.
