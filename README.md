# djangodirstruct
#Typical Django project directory structure
└── MY_PROJECT
    ├── BASE_DIR
    │   ├── MY_APP
    │   │   └── settings.py
    │   └── manage.py
    └── static        -> STATIC_ROOT
        └── static    -> STATICFILES_DIRS
# But it is not a good configuration because it mixes up collected statics and the directory where Django tries to find static files (e. g. to collect them). 

# Best Practice Directory Structure
└── MY_PROJECT
    └── BASE_DIR
        ├── my_app
        │   ├── settings.py
        │   └── static              -> STATICFILES_DIRS
        ├── manage.py
        └── deployment
            ├── collected_static    -> STATIC_ROOT
            └── media               -> MEDIA_ROOT
            
# settings.py
BASE_DIR = os.path.dirname(os.path.dirname(__file__))
STATICFILES_DIRS = (os.path.join(
    BASE_DIR, "my_app", "static"),)
STATIC_ROOT = os.path.join(
    os.path.dirname(BASE_DIR), "deployment", "collected_static")
MEDIA_ROOT = os.path.join(
    os.path.dirname(BASE_DIR), "deployment", "media")
