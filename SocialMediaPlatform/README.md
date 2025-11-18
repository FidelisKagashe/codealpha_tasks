# SocialApp - Django Social Media Platform

A full-featured social media application built with Django, featuring user profiles, posts, comments, likes, and follow system. The application includes dark/light mode toggle and uses Tailwind CSS for styling.

## Features

- **User Authentication**: Register, login, and logout functionality
- **User Profiles**: Customizable profiles with bio, profile picture, location, and website
- **Posts**: Create, view, and delete posts with optional images
- **Comments**: Comment on posts and delete your own comments
- **Likes**: Like/unlike posts
- **Follow System**: Follow/unfollow other users
- **Feed**: See posts from users you follow
- **Explore**: Discover all posts from all users
- **Dark/Light Mode**: Toggle between dark and light themes (saved in localStorage)
- **Responsive Design**: Works on mobile, tablet, and desktop

## Technology Stack

- **Backend**: Django 4.2+
- **Frontend**: HTML, Tailwind CSS, Alpine.js
- **Database**: SQLite (default)
- **Icons**: Font Awesome 6

## Installation & Setup

### Prerequisites

- Python 3.8 or higher
- pip (Python package manager)

### Installation Steps

1. **Create a virtual environment** (recommended):
```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

2. **Install dependencies**:
```bash
pip install -r requirements.txt
```

3. **Apply database migrations**:
```bash
python manage.py makemigrations
python manage.py migrate
```

4. **Create a superuser** (for admin access):
```bash
python manage.py createsuperuser
```

5. **Run the development server**:
```bash
python manage.py runserver
```

6. **Access the application**:
   - Main site: http://127.0.0.1:8000/
   - Admin panel: http://127.0.0.1:8000/admin/

## Usage

### Getting Started

1. **Register**: Create a new account at `/register/`
2. **Login**: Sign in with your credentials at `/login/`
3. **Create Posts**: Share your thoughts on the home page
4. **Explore**: Discover other users and their content
5. **Follow Users**: Visit user profiles and click "Follow" to see their posts in your feed
6. **Interact**: Like posts and leave comments

### Dark/Light Mode

Click the moon/sun icon in the navigation bar to toggle between dark and light themes. Your preference is saved automatically.

## Project Structure

```
project/
├── socialapp/              # Main project settings
│   ├── settings.py
│   ├── urls.py
│   └── wsgi.py
├── core/                   # Main application
│   ├── models.py          # Database models
│   ├── views.py           # View functions
│   ├── forms.py           # Django forms
│   ├── urls.py            # URL routing
│   └── admin.py           # Admin configuration
├── templates/             # HTML templates
│   ├── base.html
│   └── core/
│       ├── home.html
│       ├── explore.html
│       ├── profile.html
│       ├── edit_profile.html
│       ├── post_detail.html
│       ├── login.html
│       └── register.html
├── media/                 # User uploaded files
│   ├── profile_pics/
│   └── posts/
├── static/               # Static files (CSS, JS, images)
├── manage.py
└── requirements.txt
```

## Models

### Profile
- One-to-one relationship with User
- Fields: bio, profile_picture, location, website

### Post
- Author (ForeignKey to User)
- Fields: content, image, created_at, updated_at

### Comment
- Linked to Post and User
- Fields: content, created_at, updated_at

### Like
- Unique combination of User and Post
- Fields: created_at

### Follow
- Unique combination of follower and following
- Fields: created_at

## API Endpoints

- `/` - Home feed (requires login)
- `/register/` - User registration
- `/login/` - User login
- `/logout/` - User logout
- `/explore/` - Explore all posts
- `/profile/<username>/` - User profile
- `/profile/edit/` - Edit your profile
- `/post/<id>/` - Post detail with comments
- `/post/<id>/like/` - Like/unlike post (AJAX)
- `/post/<id>/delete/` - Delete post
- `/comment/<id>/delete/` - Delete comment
- `/user/<username>/follow/` - Follow/unfollow user (AJAX)

## Customization

### Changing Colors

The application uses Tailwind CSS. To customize colors, modify the classes in the template files. The primary color is blue (`blue-600`, `blue-700`, etc.).

### Adding Features

To add new features:
1. Update models in `core/models.py`
2. Create/update forms in `core/forms.py`
3. Add views in `core/views.py`
4. Define URLs in `core/urls.py`
5. Create templates in `templates/core/`

## Security Notes

- Change `SECRET_KEY` in production
- Set `DEBUG = False` in production
- Configure `ALLOWED_HOSTS` for production
- Use PostgreSQL or MySQL for production databases
- Set up proper file storage for media files in production
- Use HTTPS in production

## License

This project is open source and available for educational purposes.

## Support

For issues or questions, please open an issue on the project repository.
