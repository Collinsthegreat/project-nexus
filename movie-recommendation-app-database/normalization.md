Movie Recommendation App Database Normalization to 3NF

Goal:
This document explains how the Movie Recommendation App database schema was normalized up to the Third Normal Form (3NF).

Step 1: First Normal Form (1NF)

Criteria:

Atomic (indivisible) values

No repeating groups or arrays

Application:

All attributes in User, Movie, Favorites, Recommendations, Ratings, and Watchlist are atomic.

No multi-valued fields (e.g., email is unique and single-valued, poster_url is a single link).

All tables satisfy 1NF.

Step 2: Second Normal Form (2NF)

Criteria:

Must satisfy 1NF

No partial dependencies (i.e., non-key attributes must depend on the whole primary key)

Application:

All tables use single-column primary keys (user_id, movie_id, favorite_id, etc.).

Junction tables (Favorites, Recommendations, Ratings, Watchlist) link Users and Movies using foreign keys — no composite primary keys were needed.

No partial dependencies exist.

All tables satisfy 2NF.

Step 3: Third Normal Form (3NF)

Criteria:

Must satisfy 2NF

No transitive dependencies (i.e., non-key attributes should not depend on other non-key attributes)

Review & Adjustments:

User Table

username, email, and password_hash all depend only on user_id.

No attribute depends on another non-key attribute.

Satisfies 3NF.

Movie Table

Attributes like title, overview, release_date, and poster_url all describe the movie entity directly.

tmdb_id (external reference) is unique and independent of other attributes.

No transitive dependencies.

Compliant with 3NF.

Favorites Table

user_id and movie_id are foreign keys.

added_at directly relates to the favorite relationship.

No dependencies beyond keys.

Recommendations Table

user_id and movie_id form the relationship.

score and created_at describe the recommendation instance directly.

No transitive dependencies.

Ratings Table

rating_value and rated_at are attributes of the rating action.

No attributes depend on other non-key attributes.

Satisfies 3NF.

Watchlist Table

added_at relates only to the watchlist action.

No transitive dependencies.

Fully normalized.

Final Verdict

All tables in the Movie Recommendation App database are normalized to 3NF:

✅ Redundancies have been avoided
✅ Data integrity is preserved
✅ Relationships are maintained using foreign keys
✅ No restructuring of tables was required beyond validation
