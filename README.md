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

## Conclusion
This project will provide you with hands-on experience in GUI development, API integration, and software design principles. By following this plan, you will create a functional and user-friendly movie database application that meets your educational objectives.
