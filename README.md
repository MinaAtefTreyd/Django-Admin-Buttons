# Django-Admin-Buttons
![Django Admin Buttons](https://github.com/minaaaatef/Django-Admin-Buttons/blob/main/images/ex1.png?row=true)

This package used to add a button functionality to the change list columns in the django admin, it uses the action methods used in the ***ModelAdmin***<br>

I wrote this package as an implementation for this [article](https://medium.com/@mina.atef0/django-admin-costume-buttons-942c97c284a8), it not hard to write the button yourself



## Getting Started

1. Install the app 
```
pip install django-admin-buttons
```

2. Add the app to the ***INSTALLED_APPS*** above the admin and static apps

``` python
INSTALLED_APPS = [
    'django_admin_buttons', # add here

    'django.contrib.admin',
    'django.contrib.staticfiles',
```

3. Use the button as needed
``` python
from django.contrib import admin
from django_admin_buttons.admin_button import AdminActionButton


def Test_function(modeladmin, request, queryset):
    # write you implementation here
    pass 

class AdminTest(admin.ModelAdmin):
    # add the button 
    list_display = ('id', 'name', 'button') 
    
    # register the function
    actions = [Test_function] 
    
    # create the function that displays the button
    @admin.display()
    def button(self, obj):
        return AdminActionButton(obj.id, 'Test_function', disabled = False, Class='btn-primary', label=None).render()

```

BUTTON PARAMETERS
``` python
AdminActionButton(id, action_name=None, url=None, disabled="", Class='btn-primary', label=None, confirm=True):
```

Explanation of the parameters:
- **id**: the object id
- **action_name**: the action name that you want to call
- **url**: the url that you want to redirect to
- **disabled**: if you want to disable the button
- **Class**: the button class
- **label**: the button label
- **confirm**: if you want to show a confirmation message before executing the action

