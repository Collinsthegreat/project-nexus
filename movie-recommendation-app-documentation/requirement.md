Movie Recommendation App – Requirements Documentation

This document outlines the technical and functional requirements for the Movie Recommendation App backend. Each feature specification includes API endpoints, input/output formats, validation rules, and performance expectations.

1. User Authentication
Functional Requirements

Allow users to register and log in securely.

Support password hashing and JWT-based authentication.

Store user profile data for personalization.

API Endpoints

POST /api/v1/auth/register
Registers a new user.

Input (JSON):

{
  "username": "moviefan123",
  "email": "fan@example.com",
  "password": "StrongPass123!"
}


Validations:

Email must be unique and properly formatted.

Username must be unique, 3–30 characters.

Password must be at least 8 characters and securely hashed.

Response (201 Created):

{
  "message": "User registered successfully.",
  "user_id": "uuid"
}


POST /api/v1/auth/login
Authenticates user and returns a JWT token.

Input:

{
  "email": "fan@example.com",
  "password": "StrongPass123!"
}


Response (200 OK):

{
  "token": "jwt-token",
  "username": "moviefan123"
}


Performance:

Password hashing must complete in <500ms.

Token generation within 200ms.

2. Movie Discovery
Functional Requirements

Fetch trending movies from TMDb API.

Fetch personalized recommendations for logged-in users.

Support pagination for large results.

API Endpoints

GET /api/v1/movies/trending
Fetches trending movies from TMDb API.

Response (200 OK):

[
  {
    "movie_id": "12345",
    "title": "Inception",
    "release_date": "2010-07-16",
    "rating": 8.8,
    "poster_url": "https://image.tmdb.org/t/p/inception.jpg"
  }
]


GET /api/v1/movies/recommendations
Fetches personalized recommendations for the logged-in user.

Response (200 OK):

[
  {
    "movie_id": "67890",
    "title": "Interstellar",
    "release_date": "2014-11-07",
    "rating": 8.6,
    "poster_url": "https://image.tmdb.org/t/p/interstellar.jpg"
  }
]


Performance:

External API requests must complete in <2s.

Cache results for trending movies for 15 minutes to reduce API calls.

3. Favorites Management
Functional Requirements

Users can save movies to their favorites list.

Users can retrieve and manage their favorite movies.

API Endpoints

POST /api/v1/favorites
Saves a movie to the user’s favorites.

Input (JSON):

{
  "movie_id": "12345"
}


Response (201 Created):

{
  "message": "Movie added to favorites.",
  "movie_id": "12345"
}


GET /api/v1/favorites
Retrieves all favorite movies for the logged-in user.

Response (200 OK):

[
  {
    "movie_id": "12345",
    "title": "Inception",
    "poster_url": "https://image.tmdb.org/t/p/inception.jpg"
  }
]


DELETE /api/v1/favorites/:movie_id
Removes a movie from favorites.

Response (200 OK):

{
  "message": "Movie removed from favorites."
}


Performance:

Favorites operations should respond in <500ms.

4. Admin Tools (Optional / Future Scope)
Functional Requirements

Monitor system health and API usage.

Manage user accounts (ban, activate, reset password).

API Endpoints (Planned)

GET /api/v1/admin/users → Retrieve all users.

DELETE /api/v1/admin/users/:id → Remove a user.

Notes

All endpoints are versioned under /api/v1/.

JWT authentication required for protected routes.

External movie data is fetched from TMDb API.

Dates follow YYYY-MM-DD format.

Author: Abuchi Collins
Project: ALX Movie Recommendation App
