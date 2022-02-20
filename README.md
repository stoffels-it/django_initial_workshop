# django_initial_workshop

## current manual steps in running container:

add to settings.py:
```
AUTH_USER_MODEL = 'core.Person'

INSTALLED_APPS = [
    'admin_reorder',
    'crispy_forms',
    'django_registration',
    'phone_field',
    'core.apps.CoreConfig',
...

DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql',
	'NAME': 'dockerws',
        'USER': 'dockerws',
        'PASSWORD': 'dockerws',
        'HOST': '127.0.0.1',
        'PORT': '5432',
    }
}
```
TODO: add option for superuser being active on create

execute:
```
python3 manage.py makemigrations core
python3 manage.py migrate core
python3 manage.py migrate
```

create urls in <project>/urls.py, add "include" to "import path":
```
import path, include

    path('', include('core.urls')),
    path('accounts/company_register/', CompanyRegistrationView.as_view(
        form_class=CompanySignUpForm),
        name='django_company_register',
    ),
    path('accounts/', include('django_registration.backends.activation.urls')),
    path('accounts/', include('django.contrib.auth.urls')),
    path('admin/', admin.site.urls),
```

create a superuser for login into backend (127.0.0.1/admin):

```
python3 manage.py createsuperuser
```
