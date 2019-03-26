---
layout: post
title:  "Five Python 3 features that you can start to use right now"
date:   2019-03-17 00:00:00 -0200
categories: python
---

2020 is close and with it, the end of life of Python 2. The first
Python 3 release completed [10 years][1] last year. However, [25%][2]
of Python developers are still using Python 2.

If you previously had experience with Python 3, the features that I
will present here aren't new for you, but if somehow you just jumped
into a Python 3 code base, these five features can be handy.
They are somewhat focused on readability.


# 1- f-strings

I like Python string formatting.

```python
# Python 2
>>> first_name = 'John'
>>> last_name = 'Doe'
>>> 'Hi! My name is %s %s.' % (first_name, last_name)
'Hi! My name is John Doe.'

>>> 'Hi! My name is {0} {1}.'.format(first_name, last_name)
'Hi! My name is John Doe.'

>>> 'Hi! My name is {first_name} {last_name}.'.format(first_name=first_name, last_name=last_name)
'Hi! My name is John Doe.'
```

But Python 3 made it even better. Now we can archive the samething
using `f-strings`:

```python
# Python 3
>>> first_name = 'John'
>>> last_name = 'Doe'
>>> f'Hi! My name is {first_name} {last_name}.'
'Hi! My name is John Doe.'
```

Python 2 examples are still valid. Make sure to choose what's better
for your use case.

# 2- Dictionary merge
If you find yourself trying to merge two dictionaries, you might end
up in this thread on [StackOverFlow][3].

```python
# Python 2
def merge_two_dicts(x, y):
    z = x.copy()   # start with x's keys and values
    z.update(y)    # modifies z with y's keys and values & returns None
    return z

z = merge_two_dicts(x, y)

# Python 2:
z = {k: v for d in (x, y) for k, v in d.items()
```

Python 3 makes it easier to just:

```python
# Python 3

>>> x = {'a': 1, 'b': 2}
>>> y = {'b': 3, 'c': 4}

>>> z = {**x, **y}
>>> z
{'a': 1, 'b': 3, 'c': 4}

```


# 3- Unpacking

We already can do this:

```python
# Python 2
>>> a, b = range(2)
>>> a
0
>>> b
1
```

Now, we can do this:

```python
# Python 3
>>> a, b, *rest = range(10)
>>> a
0
>>> b
1
>>> rest
[2, 3, 4, 5, 6, 7, 8, 9]
```

In practice?

```python
# Python 3
>>> first_line, *_, last_line = open('./myfile.txt').readlines()
>>> print(first_line)
'My first line\n'
>>> print(last_line)
'My last line\n'

```


# 4- Simpler constructor

In Python 3, we don't need to invoke the `super` function with the
current class anymore.

So, instead of:
```python
# Python 2:
class MyClass(MySuperClass):
    def __init__(self, *args, **kwargs):
        super(MyClass, self).__init__(args, kwargs)
```

Now we can just:

```python
# Python 3:
class MyClass(MySuperClass):
    def __init__(self, *args, **kwargs):
        super().__init__(args, kwargs)
```


# 5- Enforce keyword-only arguments in functions
Take a second. Can you identify the "problem" with this function?

```python
# Python 2:
def create_user(email, password, is_active=True, is_valid=True, group=None):
    pass

>>> create_user('user@local.com', '12345', True, True, 'Admin')
```

I'll say to you. It's not explicit. It makes hard understand what all
these parameters means, and there's no way to enforce the keywords
parameters to be used with Python 2. Until now:

```python
# Python 3
def create_user(*, email=None, password=None, is_active=True, is_valid=True, group=None):
    pass

# Now, if we try to invoke:
>>> create_user('user@local.com', '12345', True, True, 'Admin')
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: create_user() takes 0 positional arguments but 2 were given

# It should be invoke using keyword arguments only.
create_user(email='email@local.com', password='1234', group=True)
```

We still can, if we want to, keep the first and second as positional
arguments and turn the keyword arguments to be used as mandatory.

```python
# Python 3
def create_user(email, password, *, is_active=True, is_valid=True, group=None):
    pass

>>> create_user('email@local.com', 'password', False, False)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: create_user() takes 2 positional arguments but 4 were given

# We need to do this, now:
>>> create_user('email@local.com', 'password', is_active=False, is_valid=False)
```


## Conclusion
Python 3 has some very nice features that you can start to use right
now. If you got interested, I recommend take a look on
[@asmeurer's][4] [presentation][5].



### References:
- <https://legacy.python.org/dev/peps/pep-0373/>
- <https://www.jetbrains.com/research/python-developers-survey-2017/>
- <https://stackoverflow.com/questions/38987/how-to-merge-two-dictionaries-in-a-single-expression>
- <https://dbader.org/blog/cool-new-features-in-python-3-6>
- <https://www.asmeurer.com/python3-presentation/slides.html>
- <http://www.informit.com/articles/article.aspx?p=2314818>
- <https://github.com/arogozhnikov/python3_with_pleasure>


<!-- Links -->
[1]: https://www.python.org/download/releases/3.0/
[2]: https://www.jetbrains.com/research/python-developers-survey-2017/
[3]: https://stackoverflow.com/questions/38987/how-to-merge-two-dictionaries-in-a-single-expression
[4]: https://twitter.com/asmeurer
[5]: https://www.asmeurer.com/python3-presentation/slides.html
