# Movieist

Movieist is a full-stack movie discovery application inspired by IMDb. Browse a collection of movies, watch trailers, and share reviews.

## Features

- Browse movies with poster artwork, genres, release dates, and backdrops
- View an individual movie's trailer
- Read existing reviews and submit a new review
- REST API backed by MongoDB

## Tech stack

| Area | Technologies |
| --- | --- |
| Frontend | React 18, React Router, Axios, Bootstrap, Material UI |
| Backend | Java 17, Spring Boot 3, Spring Data MongoDB, Maven |
| Database | MongoDB Atlas / MongoDB |

## Project structure

```text
movieist/
├── frontend/movie-gold-v1/  # React client
└── backend/movieist/        # Spring Boot REST API
```

## Getting started

### Prerequisites

- Node.js and npm
- Java 17+
- MongoDB database (local or Atlas)

### 1. Configure the backend

The backend reads its database settings from environment variables. Set the following values before starting it:

```text
MONGO_DATABASE=movieist
MONGO_USER=your_mongodb_username
MONGO_PASSWORD=your_mongodb_password
MONGO_CLUSTER=your-cluster-url
```

For MongoDB Atlas, `MONGO_CLUSTER` is the cluster host and query string after `@`, for example:

```text
cluster0.example.mongodb.net/?retryWrites=true&w=majority
```

Start the API:

```bash
cd backend/movieist
./mvnw spring-boot:run
```

On Windows PowerShell:

```powershell
cd backend/movieist
.\mvnw.cmd spring-boot:run
```

### 2. Configure and start the frontend

Install dependencies and run the React development server:

```bash
cd frontend/movie-gold-v1
npm install
npm start
```

The client opens at [http://localhost:3000](http://localhost:3000).

Before using a local backend, update `frontend/movie-gold-v1/src/api/axiosConfig.js` so `baseURL` points to the address where the API is running, such as `http://localhost:8080`.

## API endpoints

| Method | Endpoint | Description |
| --- | --- | --- |
| `GET` | `/api/v1/movies` | Return all movies |
| `GET` | `/api/v1/movies/{imdbId}` | Return a movie by IMDb ID |
| `POST` | `/api/v1/reviews` | Create a review for a movie |

Example review request:

```json
{
  "reviewBody": "An excellent movie with a memorable soundtrack.",
  "imdbId": "tt3915174"
}
```

## Available scripts

From `frontend/movie-gold-v1`:

```bash
npm start       # Run the development server
npm test        # Run frontend tests
npm run build   # Create a production build
```

From `backend/movieist`:

```bash
./mvnw test              # Run backend tests
./mvnw spring-boot:run   # Start the API
```

## Data

`backend/movieist/_data/movies.json` contains seed movie data that can be imported into a MongoDB `movies` collection.

## License

This project is available for learning and personal use. Add a license file before distributing it publicly.
