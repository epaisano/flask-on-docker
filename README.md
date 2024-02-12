# Flask on Docker


## Overview

This repo is meant to recreate an instagram tech stack. From the tutorial found [here](https://testdriven.io/blog/dockerizing-flask-with-postgres-gunicorn-and-nginx/), we were able to dockerize our Flask app. For production, we used Nginx and Gunicorn. Finally, to test our app, we uploaded our choice of gif, found underneath:

https://github.com/epaisano/flask-on-docker/assets/123110785/48291328-55a0-4df9-83f4-5d921de34c15

A more clear version of this gif can be found on [this](https://github.com/epaisano/flask-on-docker/assets/123110785/d288b103-35f1-4a2f-873d-731b7c64972d) video.


**Development**

This uses the default Flask development server. 

    1. Rename .env.dev-sample to .env.dev.
    2. Build the images and run the containers:
    ```
    docker-compose -f docker-compose.prod.yml up -d --build
    docker-compose -f docker-compose.prod.yml exec web python manage.py create_db
    ```
    Then, test it out at [http://localhost:6272](http://localhost:6272). Your code changes should apply automatically because your "web" folder is mounted into the container.


**Production**

This part uses gunicorn + nginx.

    1. Rename .env.prod-sample to .env.prod and .env.prod.db-sample to .env.prod.db. Update the environment variables.
    2. Build the images and run the containers:
    ```
    docker-compose -f docker-compose.prod.yml up -d --build
    docker-compose -f docker-compose.prod.yml exec web python manage.py create_db
    ```
    Test it out at [http://localhost:6272](http://localhost:6272). To apply changes, remember to rebuild and spin up the new containers.


*The above instructions were adapted from [this](https://github.com/testdrivenio/flask-on-docker) tutorial.
