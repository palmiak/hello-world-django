# Kinsta - Hello World - Django
An example of how to set your Django application up to enable deployment on Kinsta App Hosting services.

> Kinsta’s Application Hosting is a service to run your web apps and any databases side by side in a hassle-free 
environment, tailored for developer needs and ease of use. App Hosting is currently in an invite-only beta phase, 
sign up for a test account at [kinsta.com/application-hosting](https://kinsta.com/application-hosting/).

## Dependency Management
Django is a Python-based web framework, so during the build process Kinsta will automatically install dependencies 
defined in your `requirements.txt` file.

The `python manage.py collectstatic` command will also be executed at every build to collect all static files to 
the 
directory defined in `STATIC_ROOT`.

## Environment Variables

Note that the `SECRET_KEY` should not be stored in your repository, but rather set up in an environment 
variable. Set a random string in your newly created app's Settings > Environment variables section and make it 
available as both build and runtime variables. Finally, redeploy your application on the Deployments page to 
make the changes effective.

## Web Server Setup

### Start Command
When deploying an application Kinsta will automatically create a processes based on the Procfile in the root of 
the repository. Make sure to use this command to run your server:

```
web: gunicorn helloworld.wsgi
```
