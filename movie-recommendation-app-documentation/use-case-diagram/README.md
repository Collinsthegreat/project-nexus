Use Case Diagram – Movie Recommendation Backend

The use case diagram illustrates the core interactions between system users (regular users, potential admin roles) and external services (TMDb API) with the key functionalities of the Movie Recommendation backend.

It highlights major user actions such as authentication, browsing trending movies, receiving recommendations, and managing favorites. Each actor is mapped to the relevant features they can access, while system interactions with TMDb and caching mechanisms provide additional context.

This diagram serves as a high-level reference for developers, designers, and stakeholders to clearly understand how end-users engage with the system and how external services integrate into the workflow.

Key Highlights

User Interactions

Registering and logging in to the system.

Browsing trending and recommended movies.

Saving and retrieving favorite movies.

System Behaviors

Secure authentication with JWT.

TMDb API integration for trending and recommended content.

Redis caching to enhance performance and reduce latency.

External Services

TMDb API for real-time movie data.

PostgreSQL for user and favorites data persistence.

✅ The use case diagram provides a clear, functional overview of the system’s scope and forms the foundation for writing detailed user stories and designing workflows.
