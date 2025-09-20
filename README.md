ALX Movie Recommendation Backend

A scalable, intelligent, and secure Django-based backend for personalized movie recommendations with REST and GraphQL API support.

Project Overview

The Movie Recommendation Backend is built with Django and Django REST Framework as part of the ALX ProDev program. It powers a recommendation system that provides users with personalized movie suggestions, search functionality, and user interaction tracking. Designed with scalability, performance, and modern API practices in mind, it serves as a strong foundation for any content recommendation platform.

Tech Stack

Backend Framework: Django 5.2.6+

Database: PostgreSQL (via psycopg)

API:

Django REST Framework with SimpleJWT

Graphene-Django for GraphQL API

Recommendation Engine:

Hybrid approach (content-based + collaborative filtering)

Asynchronous background tasks with Celery + Redis

Documentation:

DRF Spectacular (OpenAPI 3.0)

GraphQL Playground

Monitoring: Sentry SDK

Code Quality: Black, Ruff, mypy

Table of Contents

Project Overview

Tech Stack

Features

Core Functionality

Security

API Features

Development Tools

Project Structure

API Documentation

REST API

GraphQL API

Authentication

Available Endpoints

Authentication

User Profile

Movies & Recommendations

Testing

Development Workflow

Contributing

License

Support

Features
Core Functionality

Base Models: Audit-stamped models for consistent metadata (created_at, updated_at, created_by, updated_by, is_active)

User Profiles: Custom user model with preferences, watch history, and ratings

Movie Catalog: Metadata-driven movie model (genres, release year, cast, directors, etc.)

Recommendation Engine:

Content-based filtering (recommend movies similar to those watched/rated)

Collaborative filtering (recommend movies based on similar users)

Hybrid scoring for balanced recommendations

Search & Filtering: Search by title, genre, rating, release year

Security

JWT Authentication with refresh tokens

Rate limiting and throttling

CORS and CSRF protection

Secure password validation

Request/Response logging

API Features

Dual API Support:

RESTful API with standardized responses

GraphQL API for flexible queries

Authentication:

JWT authentication with refresh tokens

Social login (OAuth2) (coming soon)

Email verification & password reset flow

Advanced Features:

Rate limiting and throttling

Request/Response logging

Comprehensive error handling

Documentation:

Swagger/ReDoc for REST

GraphQL Playground

Development Tools

Pre-commit hooks with code formatters and linters

Comprehensive test suite with pytest

Code coverage reports

Django Debug Toolbar for dev mode

Type checking with mypy

Project Structure
movie_recommendation_backend/
├── apps/
│   ├── accounts/               # Authentication & user profile management
│   ├── movies/                 # Movie catalog, metadata, and ratings
│   ├── recommendations/        # Recommendation engine logic
│   └── core/                   # Core shared utilities and base classes
├── docs/                       # API & project documentation
├── backend/                    # Main project folder
│   ├── settings/               # Environment-based settings
│   ├── urls.py                 # Root URL configuration
│   ├── schema.py               # GraphQL schema
│   └── wsgi.py / asgi.py
├── logs/                       # Application logs
├── media/                      # Uploaded files (if any)
├── requirements/               # Dependency management
├── tests/                      # Unit & integration tests
├── docker-compose.yml
├── Dockerfile
├── manage.py
└── README.md

API Documentation
REST API

Swagger: /schema/swagger-ui/

ReDoc: /schema/redoc/

GraphQL API

GraphQL Playground: /graphql/

Supports queries, mutations, and (coming soon) subscriptions

Authentication

Both REST and GraphQL APIs use JWT-based authentication.
Include your access token in the header:

Authorization: Bearer <your_access_token>

Available Endpoints
Authentication (REST)

POST /api/v1/accounts/register/ – Register a new user

POST /api/v1/accounts/login/ – Login and get tokens

POST /api/v1/accounts/logout/ – Invalidate refresh token

POST /api/v1/accounts/token/refresh/ – Refresh access token

GET /api/v1/accounts/me/ – Get user profile

PATCH /api/v1/accounts/me/ – Update profile

Movies & Recommendations (REST)

GET /api/v1/movies/ – List all movies

GET /api/v1/movies/<id>/ – Get details of a movie

POST /api/v1/movies/<id>/rate/ – Rate a movie

GET /api/v1/recommendations/ – Get personalized recommendations

Example GraphQL Queries

Get recommendations:

query {
  recommendations {
    id
    title
    genres
    score
  }
}


Rate a movie:

mutation {
  rateMovie(movieId: 1, rating: 5) {
    ok
    errors
    rating {
      movie {
        title
      }
      value
    }
  }
}

Testing

Run the full test suite:

pytest

Development Workflow

Create a new branch for your feature

Write tests for your changes

Implement the feature

Run tests and ensure all pass

Commit & push changes

Open a Pull Request

Contributing

Fork the repository

Create your feature branch (git checkout -b feature/amazing-feature)

Commit changes (git commit -m 'Add some amazing feature')

Push to branch (git push origin feature/amazing-feature)

Open a Pull Request

License

This project is licensed under the MIT License – see the LICENSE file for details.

Support

For support, please open an issue in the repository or contact the maintainers.
