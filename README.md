# Django user authentication app using JWT

This repository is to plug and play user authentication with JWT in Django.

Authentication tutorial: https://youtu.be/PUzgZrS_piQ

1. Simply copy "users" app (folder) in your project.
2. For JWT Authentication you need to install
`pip install djangorestframework`
`pip install django-cors-headers`
`pip install pyJWT`

I have attached requirements.txt for reference. But try not using it to install packages.

3. In settings.py

```
INSTALLED_APPS=[
...
'rest_framework',
'corsheaders',
'users',
]

...


MIDDLEWARE=[
...
'django.contrib.sessions.middleware.SessionMiddleware',
'corsheaders.middleware.CorsMiddleware', # this one must be added and at this position only
'django.middleware.common.CommonMiddleware',
...
]

...

AUTH_USER_MODEL = 'users.User'

CORS_ORIGIN_ALLOW_ALL = True
CORS_ALLOW_CREDENTIALS = True
```

4. In main project's urls.py add following:
    `path('auth/', include("users.urls")),`