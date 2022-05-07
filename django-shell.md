
## Here's a transcript of work we did in the Django shell

To open the django shell, type `python manage.py shell`. Then, be sure to import the models you want to work with.

```sh
❯ python manage.py shell
Python 3.10.2 (main, Feb 16 2022, 15:41:47) [Clang 13.0.0 (clang-1300.0.29.30)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
(InteractiveConsole)
>>> from contacts.models import Contact, Note
>>> Contact.objects.all()
<QuerySet [<Contact: Belletrix>, <Contact: Adam Gori>]>
>>>trix = Contact.objects.get(pk=1)
>>> trix
<Contact: Belletrix>
>>> trix.name
'Belletrix'
>>> trix.birthday
datetime.date(1988, 6, 2)
>>> trix.phone_number
'2126285331'
>>> Note.objects.all()
<QuerySet [<Note: This is my chihuahua>, <Note: Another note: she li>, <Note: This is my husband>, <Note: He likes to cook din>, <Note: Hey this is about be>]>
>>> Note.objects.get(contact_id=1)
Traceback (most recent call last):
  File "<console>", line 1, in <module>
  File "/Users/amygori/.local/share/virtualenvs/django-uptact-amygori-XkbDyQPd-python/lib/python3.10/site-packages/django/db/models/manager.py", line 85, in manager_method
    return getattr(self.get_queryset(), name)(*args, **kwargs)
  File "/Users/amygori/.local/share/virtualenvs/django-uptact-amygori-XkbDyQPd-python/lib/python3.10/site-packages/django/db/models/query.py", line 439, in get
    raise self.model.MultipleObjectsReturned(
contacts.models.Note.MultipleObjectsReturned: get() returned more than one Note -- it returned 3!
>>> Note.objects.filter(contact_id=1)
<QuerySet [<Note: This is my chihuahua>, <Note: Another note: she li>, <Note: Hey this is about be>]>
>>> trix.notes
<django.db.models.fields.related_descriptors.create_reverse_many_to_one_manager.<locals>.RelatedManager object at 0x1048cb760>
>>> trix.notes.all()
<QuerySet [<Note: This is my chihuahua>, <Note: Another note: she li>, <Note: Hey this is about be>]>
>>> Note.objects.first()
<Note: This is my chihuahua>
>>> Note.objects.first().contact
<Contact: Belletrix>
>>> Note.objects.first().contact.name
'Belletrix'
>>>
```
