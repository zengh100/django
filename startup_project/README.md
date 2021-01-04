Hello world Project with Django

# 1. Create folder to new projects
`mkdir myDjango`
cd  myDjango

# 2. Setup environment
# create virtual env for this project
conda create -n django python=3.7
# enter into the virtual env
conda activate django
# conda install anacoda django
conda install -c anaconda django 
# double check pyhton version
python --version
# list files and folders
ls

# 3. Create a new project (under folder myDjango)
# start a project (name is startup_project)
django-admin startproject startup_project
# list files and folders. you should see new folder "startup_project"
ls
cd startup_project/
# start server to see if everything is so far so good
python manage.py runserver
# now enter this to a browser: http://127.0.0.1:8000/

# 4. Add view display "Hello, World!"
python manage.py startapp hello
# check if a new folder "hello" is created?
ls hello/
# now edit two files hello/views.py and startup_project/urls.py
# add below to hello/views.py
```python
from django.http import HttpResponse

# Create your views here.
def myView(request):
    return HttpResponse('Hello, World!')
```
# make below changes to startup_project/urls.py
```python
from hello.views import myView

urlpatterns = [
    path('admin/', admin.site.urls),
    path('sayHello/', myView),
]
```
# 5.Test
# start server again
python manage.py runserver
# now enter this to a browser: http://127.0.0.1:8000/sayHello
