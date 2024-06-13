1)To install the Django Debug Toolbar, you can use pip:
pip install django-debug-toolbar


2)Add to Installed Apps: Add 'debug_toolbar' to the INSTALLED_APPS in your Django settings:

INSTALLED_APPS = [
    # ...
    'debug_toolbar',
]

3)Add Middleware: Add the debug toolbar middleware to the MIDDLEWARE setting:

MIDDLEWARE = [
    # ...
    'debug_toolbar.middleware.DebugToolbarMiddleware',
]

4)Internal IPs: Specify internal IP addresses for which the toolbar should be displayed(In settings.py file):

INTERNAL_IPS = [
    '127.0.0.1',
    # add more IPs as needed
]

5)URL Configuration: Include the debug toolbar URLs in your project's URL configuration(in urls.py in project):

from django.conf import settings
from django.urls import include, path

if settings.DEBUG:
    import debug_toolbar
    urlpatterns = [
        path('__debug__/', include(debug_toolbar.urls)),
        # your other paths
    ]
_______________________________________________________________________________________________________________________________________________________________________________________________________
Usage
When you run your Django development server, the toolbar will appear on the right side of your browser window. The toolbar provides a wealth of information, including:

SQL Queries: Number of queries executed, time taken, and details about each query.
Settings: Django settings in use.
Headers: HTTP request and response headers.
Request Vars: GET and POST variables.
Template: Templates used in rendering the page and context variables.
Static Files: Information about static files.
Signals: Signals sent during the request/response cycle.
Logging: Log messages.
_______________________________________________________________________________________________________________________________________________________________________________________________________
6)Customization
You can customize the Django Debug Toolbar by adding a DEBUG_TOOLBAR_CONFIG dictionary to your settings. For example(in settings.py):

DEBUG_TOOLBAR_CONFIG = {
    'SHOW_TOOLBAR_CALLBACK': lambda request: True,  # Always show toolbar
    'INTERCEPT_REDIRECTS': False,  # Don't intercept redirects
}

7)Panels
The toolbar's functionality is split into panels, and you can enable or disable them in your settings(in settings.py):

DEBUG_TOOLBAR_PANELS = [
    'debug_toolbar.panels.timer.TimerPanel',
    'debug_toolbar.panels.settings.SettingsPanel',
    'debug_toolbar.panels.headers.HeadersPanel',
    'debug_toolbar.panels.request.RequestPanel',
    'debug_toolbar.panels.sql.SQLPanel',
    'debug_toolbar.panels.templates.TemplatesPanel',
    'debug_toolbar.panels.staticfiles.StaticFilesPanel',
    'debug_toolbar.panels.cache.CachePanel',
    'debug_toolbar.panels.signals.SignalsPanel',
    'debug_toolbar.panels.logging.LoggingPanel',
    'debug_toolbar.panels.redirects.RedirectsPanel',
]

