# Movie Recommendation System

## Overview
A personalized movie recommendation system that analyzes user preferences and viewing history to suggest relevant films. The system employs collaborative filtering and content-based algorithms to provide tailored movie recommendations.

## Table of Contents
- [Features](#features)
- [Technology Stack](#technology-stack)
- [Installation](#installation)
- [Usage](#usage)
- [API Reference](#api-reference)
- [Dataset](#dataset)
- [Algorithm](#algorithm)
- [Contributing](#contributing)
- [License](#license)

## Features
- Personalized movie recommendations based on user preferences
- Search functionality for movies by title, genre, actor, or director
- User rating system to improve future recommendations
- Similar movie suggestions based on content similarity
- Trending and popular movie lists
- User watchlist and favorites management

## Technology Stack
- **Backend**: Python with Flask/Django
- **Frontend**: Streamlit
- **Database**: SQLite/PostgreSQL
- **ML Libraries**: Scikit-learn, TensorFlow
- **Data Processing**: Pandas, NumPy, NLTK

## Installation

### Prerequisites
- Python 3.8+
- pip (Python package manager)
- Node.js and npm (if using a JavaScript frontend)

### Setup Steps
1. Clone the repository
```bash
git clone https://github.com/yourusername/movie-recommendation-system.git
cd movie-recommendation-system
```

2. Set up a virtual environment
```bash
python -m venv venv
source venv/bin/activate  # On Windows, use: venv\Scripts\activate
```

3. Install dependencies
```bash
pip install -r requirements.txt
```

4. Set up the database
```bash
python manage.py migrate  # If using Django
# or
python init_db.py  # If using a custom script
```

5. Load movie data
```bash
python load_data.py
```

6. Start the server
```bash
python app.py  # Or python manage.py runserver for Django
```

## Usage

### Basic Usage
1. Register a new account or login to your existing account
2. Rate at least 10 movies to get initial recommendations
3. Browse recommended movies on your dashboard
4. Search for specific movies using the search functionality
5. Add movies to your watchlist
6. Rate movies after watching to improve future recommendations

### Example Code Snippet
```python
# Get recommendations for a user
from recommender.engine import RecommenderEngine

engine = RecommenderEngine()
recommendations = engine.get_recommendations(user_id=123, limit=10)
print(recommendations)
```

## API Reference

### Authentication
```
POST /api/auth/login
POST /api/auth/register
GET /api/auth/logout
```

### Movies
```
GET /api/movies - List all movies (with pagination)
GET /api/movies/{id} - Get details of a specific movie
GET /api/movies/search?q={query} - Search for movies
```

### Recommendations
```
GET /api/recommendations - Get personalized recommendations
GET /api/recommendations/similar/{movie_id} - Get similar movies
GET /api/recommendations/trending - Get trending movies
```

### User Data
```
GET /api/user/watchlist - Get user's watchlist
POST /api/user/watchlist - Add movie to watchlist
DELETE /api/user/watchlist/{movie_id} - Remove movie from watchlist
POST /api/user/ratings - Rate a movie
```

## Dataset
The system uses the [MovieLens](https://grouplens.org/datasets/movielens/) dataset, which includes:
- 100,000+ ratings from 1,000+ users on 1,700+ movies
- Movie metadata including titles, genres, and release dates
- User demographic information

For production use, consider licensing from commercial movie databases like TMDB or IMDB for more comprehensive and up-to-date data.

## Algorithm
The recommendation system employs a hybrid approach combining:

1. **Collaborative Filtering**: Recommends movies based on similar users' preferences
   - User-based: Finding users with similar taste
   - Item-based: Finding movies similar to those the user liked

2. **Content-Based Filtering**: Recommends movies with similar attributes to those the user liked
   - Features include genre, director, actors, and plot keywords

3. **Matrix Factorization**: Uses techniques like Singular Value Decomposition (SVD) to identify latent factors in user-movie interactions

## Contributing
Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

Please make sure to update tests as appropriate and follow the code style guidelines.

## License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
