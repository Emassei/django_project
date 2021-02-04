# Less of a README and more of NOTES
## Database SQLite

```
# Get into the DB sqlite
$ sqlite3 path_to_db

.show	    Displays current settings for various parameters
.databases	Provides database names and files
.quit		Quit sqlite3 program
.tables		Show current tables
.schema		Display schema of table
.header		Display or hide the output table header
.mode		Select mode for the output table
.dump		Dump database in SQL text format

# write normal sql queries

select * from table_name

# get all columns
PRAGMA table_info(polls_choice);
```

## Django Models

```
class Choice(models.Model):
    question = models.ForeignKey(Question, on_delete=models.CASCADE)


# CASCADE: When the referenced object is deleted, also delete the objects that
# have references to it (when you remove a blog post for instance, you might want
# to delete comments as well). SQL equivalent: CASCADE.

class Question(models.Model):
    def __str__(self):
        return self.question_text

# def_str__ function is called whenever str() on an object. From the ORM, you can see
# you can see it when you call Question.objects.all(), i.e. Class.objects.all()
```

## Migrations

```
$ python manage.py makemigrations polls

# By running makemigrations, you’re telling Django that you’ve made some changes to your models (in this case,
# you’ve made new ones) and that you’d like the changes to be stored as a migration.

# This does not create a migration in the DB, or change the schema in any way, it just creates the file
# which will be used to make those changes.



$ python manage.py sqlmigrate polls 0001
# This will simply output the sql you are about to run

$ python manage.py migrate
# Actually makes the changes to the DB
```


