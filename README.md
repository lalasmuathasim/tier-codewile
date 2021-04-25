# tier-codewile

Tier-codewile repository is the backend api part for the codewile.com. This api application is a decoupled django application that serve GraphQL endpoint to the codewile.com frontend. Codewile frontend is generated using GatsbyJS.

## How to setup the tier-codewile for the local development
1. Clone this repository
2. Go to the root of `tier-codewile` cloned folder
3. Create a virtual environement by running `python3 -m venv tierenv`
4. Activate the virtual environement `source tierenv/bin/activate`
5. Install Django using pip `pip install django`
6. Now using `django-admin` command initiate the project (here the project name is codewile) `django-admin startproject codewile .`
7. If you want to create a django app for the project, go to the project directory and using `django-admin` command you can initiate the app by running `django-admin startapp appname`
8. To run the application go back to the root folder where `manage.py` existes and run `python3 manage.py runserver`

*Note that the steps involved in creating virtual environement may vary in Windows machines.*

## Commiting Migrations
Django migration documentation states that
> The migration files for each app live in a “migrations” directory inside of that app, and are designed to be committed to, and distributed as part of, its codebase. You should be making them once on your development machine and then running the same migrations on your colleagues’ machines, your staging machines, and eventually your production machines

But this is entirely upto the Developers and team, if we push the migration as well there is a chance that you face many conflicts. So for convenience we can say that if you application under heavy development you may ignore the migrations and when it is ready for deployment then you can include your migrations as part of push and you can track it.

You can find a discussion about this on this [stackoverflow](https://stackoverflow.com/questions/28035119/should-i-be-adding-the-django-migration-files-in-the-gitignore-file) link

>You can run makemigrations locally and this creates the migration file. Commit this new migration file to repo. You should not run makemigrations in production at all. You can run migrate in production and you will see the migrations are applied from the migration file that you committed from local. This way you can avoid all conflicts.

>IN LOCAL ENV, to create the migration files,

>python manage.py makemigrations 
>python manage.py migrate
>Now commit these newly created files, something like below.
>`git add app/migrations/...`
>`git commit -m 'add migration files' app/migrations/...`
>IN PRODUCTION ENV, run only the below command.
>`python manage.py migrate`
