---
title: 'How to Extend User Model in Django'
date: 2022-05-15
permalink: /posts/how-to-extend-user-model-in-django/
tags:
  - python
  - django
---
Welcome to my first blog post. Tonight, I decided to share my knowledge and exprience globally using a personal blog. (I will share my exprience of creating this blog later.) I used the Django framework in several projects and saw and read lots of materials about this framework. It is one of the best web frameworks.

The most common and first things in using django framework or any web framework is to define a customizable user model. Unfortunaly or fortunatly
There are four ways to extend the user model in the Django framework. In this post, I am going to explain each of them.

1. Using a proxy model.
2. Using a profile model.
3. Extending `AbstractBaseUser`.
4. Extending `AbstractUser`.

## Using a Proxy Model

A proxy model is a kind of inheritance without creating a new table in the database. So, if you are going to just change some behaviors (methods, manager queries), this method is recommended.

```python
from django.contrib.auth.models import User

from .managers import CustomUserManager

class CustomUser(User):
    objects = CustomUserManager()

    class Meta:
        proxy = True
        ordering = ('first_name', )

    def do_something(self):
        pass
```

Since `CustomUser` is a proxy model (`proxy = True`), ``User.objects.all()` and `CustomUser.objects.all()` are identical and will hit the same table. The difference is just the behavior we define (i.e. `do_something`).

## Using a Profile Model
some details here.

## Extending AbstractBaseUser
some details here.

## Extending AbstractUser
some details here.
