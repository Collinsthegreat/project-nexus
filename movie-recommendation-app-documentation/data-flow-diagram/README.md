Data Flow Diagram – Movie Recommendation Backend

The data flow diagram (DFD) provides a structured view of how data moves through the Movie Recommendation backend system. It shows the interactions between external entities, internal processes, and data stores, ensuring transparency of how requests and responses are handled.

This diagram focuses on how users interact with the system, how data is exchanged with the TMDb API, and how the backend manages caching and persistence.

Key Highlights

External Entities

User: Initiates actions such as login, browsing, and managing favorites.

TMDb API: Provides trending and recommended movie data.

Core Processes

User Authentication: Handles registration, login, and token generation.

Fetch Trending Movies: Retrieves popular movies from TMDb and caches them.

Fetch Recommended Movies: Fetches personalized recommendations from TMDb.

Save Favorite Movies: Stores user-selected favorites in the database.

Retrieve Favorite Movies: Fetches saved favorites from the database.

Data Stores

PostgreSQL Database: Stores user credentials, accounts, and favorite movies.

Redis Cache: Stores trending and recommended movie results to improve response time.

Data Flow Examples

Authentication:
User → [Login/Signup credentials] → Authentication Process → PostgreSQL → [JWT Token] → User.

Trending Movies:
User → [Request Trending Movies] → Fetch Trending Movies → TMDb API → [Movie Data] → Redis → User.

Favorites:
User → [Save Favorite Movie] → Save Favorites → PostgreSQL.
User → [Request Favorites] → Retrieve Favorites → PostgreSQL → [Favorites List] → User.

✅ The DFD provides developers, architects, and stakeholders with a clear overview of how data is processed, cached, and persisted across the system, serving as a blueprint for backend workflows and performance optimization.
