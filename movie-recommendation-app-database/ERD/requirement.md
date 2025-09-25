ERD (Entity Relationship Diagram) – Movie Recommendation App Backend
Description

User (user_id)
↳ 1:N with Favorites (user_id)
↳ 1:N with Recommendations (user_id)
↳ 1:N with Ratings (user_id)
↳ 1:N with Watchlist (user_id)

Movie (movie_id)
↳ 1:N with Favorites
↳ 1:N with Recommendations
↳ 1:N with Ratings
↳ 1:N with Watchlist

Favorites, Recommendations, Ratings, and Watchlist act as bridge entities connecting Users and Movies.

ERD Summary
Entities & Attributes

User

user_id (PK)

username

email (Unique, Indexed)

password_hash

created_at

last_login

Movie

movie_id (PK)

title

overview

release_date

poster_url

popularity_score

tmdb_id (external reference, Unique, Indexed)

Favorites

favorite_id (PK)

user_id (FK → User.user_id)

movie_id (FK → Movie.movie_id)

added_at

Recommendations

recommendation_id (PK)

user_id (FK → User.user_id)

movie_id (FK → Movie.movie_id)

score

created_at

Ratings

rating_id (PK)

user_id (FK → User.user_id)

movie_id (FK → Movie.movie_id)

rating_value (1–5)

rated_at

Watchlist

watchlist_id (PK)

user_id (FK → User.user_id)

movie_id (FK → Movie.movie_id)

added_at

Relationships Between Entities
Entity A	Relationship	Entity B	Cardinality
User	marks	Favorites	1:N (a user can favorite many movies)
User	receives	Recommendations	1:N (a user can receive many recommendations)
User	gives	Ratings	1:N (a user can rate many movies)
User	tracks	Watchlist	1:N (a user can add many movies to their watchlist)
Movie	appears in	Favorites	1:N (a movie can be in many users’ favorites)
Movie	appears in	Recommendations	1:N (a movie can be recommended to many users)
Movie	receives	Ratings	1:N (a movie can have many ratings)
Movie	appears in	Watchlist	1:N (a movie can appear in many users’ watchlists)
ER Diagram

The image can be found in:
ERD/movie-recommendation-app-erd-diagram.png
