=====
Yapi (Yet/Why Another API Framework)
=====

Yapi is a mini-framework for Django for creating RESTful APIs.

Quick start
-----------

1. Add "yapi" to your INSTALLED_APPS setting like this:

      INSTALLED_APPS = (
          ...
          'yapi',
      )
      
2. Create a 'logs' folder on your project's folder (if you don't have one already).
      
3. Add logger handler:

      LOGGING = {
          'version': 1,
          'disable_existing_loggers': False,
          'handlers': {
            ...
            'log_file_yapi': {
                'level': 'DEBUG',
                'class': 'logging.handlers.RotatingFileHandler',
                'filename': os.path.join(os.path.join(os.path.dirname( __file__ ), '..'), 'logs/yapi.log'),
                'maxBytes': '16777216', # 16megabytes
            },
        },
        'loggers': {
            ...
            'yapi': {
                'handlers': ['log_file_yapi'],
                'propagate': True,
                'level': 'DEBUG',
            }
        }
    }
    
4. Make sure you have a 'HOST_URL' setting (e.g. 'http://localhost:8000').

5. Run `python manage.py syncdb` to create the yapi models.