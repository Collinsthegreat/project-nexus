Flowchart – Movie Recommendation Backend

The flowchart provides a step-by-step visual representation of the logical flow within the Movie Recommendation backend system. It outlines how user actions are processed, how data flows through backend services, and how results are delivered.

This diagram is especially useful for developers and stakeholders to understand the system’s behavior in sequential operations, error handling, and decision points.

Key Highlights

User Interaction Flow

Start with user authentication (login or signup).

Authenticated users proceed to request trending or recommended movies.

Users can also save or retrieve their favorite movies.

System Processes

Authentication Decision: Checks validity of credentials and issues JWT tokens.

Movie Retrieval: Determines if data is available in Redis cache. If not, fetches from TMDb API and stores results in cache.

Favorites Management: Saves and retrieves favorites from PostgreSQL.

Decision Points

Valid Credentials? → Yes: Issue token | No: Return error.

Cached Data Available? → Yes: Serve from cache | No: Fetch from TMDb API.

Endpoints

REST and GraphQL APIs serve the user with results after processing.

Example Flow

User Login:

User enters credentials → Authentication process → DB validation → Issue JWT → User proceeds.

Fetching Trending Movies:

User request → Check Redis cache → If cached, return results → Else, call TMDb API → Store in Redis → Return results.

Favorites:

User action → Save to PostgreSQL → Retrieve later when requested.

The flowchart ensures that system logic, decision paths, and error handling are clearly documented. It acts as a reference point for backend developers, QA testers, and system architects to validate workflows and ensure system reliability.
