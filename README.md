# project-joy

Delta HCM, LLC. Project Joy

## Status

Currently just documentation.  To build the documentation you need to create a
Python virtualenv and install the Sphinx requirements.  Then run ```make html```
in the docs directory.

This will generate the docs in ```docs/build/html/index.html```.

## How to run locally

1. Create a virtualenv and switch to it:

    ```
    $ mkvirtualenv project-joy
    $ workon project-joy
    ```

2. Get this project.

    First, clone the project-joy repo as origin:

    ```
    $ git clone git@github.com:deltahcm/project-joy.git
    ```

3. Make sure Postgres is installed and running.

    Easiest way to do this is download and install [Postgres.app](http://postgresapp.com/).

    ```
    $ createdb project_joy
    ```

4. Install Python requirements:

    ```
    $ cd project-joy
    $ pip install -r requirements.txt
    ```

5. Sync Django + Postgres:

    ```
    $ python manage.py syncdb
    ```

6. Install JavaScript requirements:

    ```
    $ cd project-joy
    $ node install
    ```


## Deployment

* current post-sync commands
  * collectstatic --noinput
  * rebuild_index --noinput
  * compress

To deploy to staging with the full post-sync command-list:

```
$ fab staging quickdeploy
```

.. with post-sync exclusions:

```
$ fab staging no:rebuild no:compress quickdeploy
```

or 

```
$ fab staging no:reb no:comp quickdeploy
```

To run just the post-sync jobs:

```
$ fab staging no:compress no:rebuild post
```

To deploy to production:

```
$ fab production deploy
```
