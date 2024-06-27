# Movie-Verse
#Sure! Here’s a project brief for your movie database application using PySide, PyQt5, and the TMDb API.

---

# Movie Database Application

## Project Overview
The Movie Database Application is a desktop GUI application designed to provide users with detailed information about movies, including reviews and ratings. The application will utilize the TMDb API to fetch movie data and user reviews. It is built using Python with PySide and PyQt5 for the GUI.

## Project Goals
- Develop a user-friendly desktop application for browsing and reviewing movies.
- Integrate with the TMDb API to fetch up-to-date movie information and reviews.
- Implement core functionalities including user authentication, movie search, detailed movie views, and user reviews.
- Ensure the application is modular, maintainable, and well-documented.

## Key Features
1. **User Authentication**
   - User registration
   - User login/logout
   - Password reset functionality

2. **Movie Database Management**
   - Search for movies by title
   - View detailed movie information (title, genre, director, cast, release date, synopsis, poster)
   - Fetch and display user reviews from TMDb

3. **User Interaction**
   - Allow users to rate movies
   - Allow users to write and edit their own reviews
   - Display a list of all user reviews

4. **Admin Features**
   - Add new movies (locally, for admin users)
   - Edit existing movie details (locally, for admin users)
   - Delete movies (locally, for admin users)

## Technologies Used
- **Programming Language**: Python
- **GUI Framework**: PySide2, PyQt5
- **API**: The Movie Database (TMDb) API
- **Database**: SQLite (for local user and review storage)
- **Libraries**: requests (for HTTP requests), bcrypt (for password hashing)

## Project Structure
```
project/
├── app.py
├── models/
│   └── movie.py
│   └── user.py
│   └── review.py
├── controllers/
│   └── movie_controller.py
│   └── user_controller.py
│   └── review_controller.py
├── views/
│   └── main_window.py
│   └── login_window.py
│   └── register_window.py
│   └── movie_list_window.py
│   └── movie_detail_window.py
│   └── add_movie_window.py
├── resources/
│   └── styles.qss
│   └── icons/
│       └── ...
├── database/
│   └── database_setup.py
├── utils/
│   └── helpers.py
├── tmdb_api.py
└── README.md
```

## Detailed Plan

### 1. User Authentication
- Implement user registration and login forms using PyQt5.
- Store user credentials securely in SQLite, using bcrypt for password hashing.
- Add functionality for password reset.

### 2. Movie Database Management
- Create a movie model to store movie data.
- Use TMDb API to search and fetch movie details and reviews.
- Display movie information in a detailed view.

### 3. User Interaction
- Allow users to rate and review movies.
- Store user reviews locally in SQLite.
- Display reviews alongside movie details, fetching additional reviews from TMDb.

### 4. Admin Features
- Implement functionalities for admin users to add, edit, and delete movies locally.
- Provide a separate admin interface for managing the movie database.

## Example Implementation

### TMDb API Integration
**`tmdb_api.py`**:
```python
import requests

class TMDbAPI:
    BASE_URL = "https://api.themoviedb.org/3"
    def __init__(self, api_key):
        self.api_key = api_key

    def get_movies(self, query):
        url = f"{self.BASE_URL}/search/movie"
        params = {
            "api_key": self.api_key,
            "query": query
        }
        response = requests.get(url, params=params)
        if response.status_code == 200:
            return response.json()["results"]
        else:
            response.raise_for_status()

    def get_movie_details(self, movie_id):
        url = f"{self.BASE_URL}/movie/{movie_id}"
        params = {
            "api_key": self.api_key
        }
        response = requests.get(url, params=params)
        if response.status_code == 200:
            return response.json()
        else:
            response.raise_for_status()

    def get_movie_reviews(self, movie_id):
        url = f"{self.BASE_URL}/movie/{movie_id}/reviews"
        params = {
            "api_key": self.api_key
        }
        response = requests.get(url, params=params)
        if response.status_code == 200:
            return response.json()["results"]
        else:
            response.raise_for_status()
```

### Main Window Example
**`main_window.py`**:
```python
import sys
from PySide2.QtWidgets import QApplication, QMainWindow, QAction, QListWidget, QVBoxLayout, QWidget
from tmdb_api import TMDbAPI

class MainWindow(QMainWindow):
    def __init__(self, tmdb_api):
        super().__init__()
        self.setWindowTitle("Movie Database")
        self.setGeometry(100, 100, 800, 600)

        self.tmdb_api = tmdb_api

        # Menu
        self.menu = self.menuBar()
        self.file_menu = self.menu.addMenu("File")

        self.add_movie_action = QAction("Add Movie", self)
        self.file_menu.addAction(self.add_movie_action)
        self.add_movie_action.triggered.connect(self.add_movie)

        # Movie list
        self.movie_list_widget = QListWidget()
        self.load_movies()

        # Layout
        layout = QVBoxLayout()
        layout.addWidget(self.movie_list_widget)
        container = QWidget()
        container.setLayout(layout)
        self.setCentralWidget(container)

    def load_movies(self):
        movies = self.tmdb_api.get_movies("popular")
        self.movie_list_widget.clear()
        for movie in movies:
            self.movie_list_widget.addItem(movie["title"])

    def add_movie(self):
        # Open add movie window (to be implemented)
        pass

if __name__ == "__main__":
    api_key = "your_tmdb_api_key"
    tmdb_api = TMDbAPI(api_key)

    app = QApplication(sys.argv)
    window = MainWindow(tmdb_api)
    window.show()
    sys.exit(app.exec_())
```

## Conclusion
This project will provide you with hands-on experience in GUI development, API integration, and software design principles. By following this plan, you will create a functional and user-friendly movie database application that meets your educational objectives.
