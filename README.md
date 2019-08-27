# Django Docker Boilerplate

A demo repo on how to organize a Django project using Docker and Docker Compose.<br/>
Also, it briefly shows how to use PyCharm along with this stack. 

## What's used 

* Docker + Docker Compose
* Django + Django REST Framework
* Postgres
* PyCharm

## Setup Steps

### Main:

1. Install Docker: `https://docs.docker.com/install/linux/docker-ce/ubuntu/` (check the menu on the left for other OS-s)
2. Install Docker Compose: `https://docs.docker.com/compose/install/`
3. Make sure that both have been installed:
    * `docker --version` -> e.g. `Docker version 18.09.2, build 6247962`
    * `docker-compose --version` -> e.g. `docker-compose version 1.23.2, build 1110ad01`
4. Clone the current repo somewhere and rename the `django_docker_boilerplate` folder as per your project name.

    This will become some `{project_name}`: 
5. Remove the `.git` hidden folder, as you will not want to keep working with this repo.
6. Go to the `{project_name}`:<br/>

    `cd {project_name}`

7. Create a Django project using:<br/> 
    `sudo docker-compose run web django-admin startproject {project_name} .`
    
    You shall see `{project_name}/manage.py` file and `{project_name}/{project_name}` folder created as a result. 

8. Take `{project_name}/_backup/ita_project/settings.py + urls.py` to your `{project_name}/{project_name}` (replace same existing files in fact)
9. Run `docker-compose -f docker-compose.yaml -f docker-compose.setup.yaml up`
    
    This will update your project pip dependencies and will run Django model migrations.
    
    Note: **use this command every time you have dependencies updated / model migrations changed** 
    
    You can check that your server is now working in a browser:
        `http://127.0.0.1:8000/users/`
    Press `Ctrl+C` when completed to stop the services. 
10. From now on you can use `docker-compose up` to run the server from a terminal. Or you can follow the PyCharm steps to work via PyCharm. 

### PyCharm:
1. Create a Python project with your upper `{project_name}` as the content root.      
2. Setup the project interpreter (see the screencast `04:00-04:50`) from docker compose.
3. Setup the Run/Debug configuration (screencast `04:50-05:15`) correspondingly.

    You want to have a `{project_name}` Run/Debug Django server configuration created as a result. 

4. Use `Run > Run {project_name}` to launch your services from Pycharm (screencast `04:50-05:55`)
5. Use `Run > Debug {project_name}` to debug your services from Pycharm (screencast `05:58-07:00`)
        
### Cleanup: 
Remove `{project_name}/{_backup}` dir as you don't need it anymore

### Notes:
You might find out that `docker/docker-compose` commands do not work out for you without the `sudo` prefix.<br/>
In that case please follow the `https://askubuntu.com/questions/477551/how-can-i-use-docker-without-sudo` advice, preferrably the `sudo usermod -aG docker $USER` 

## External docs
* Screencast https://drive.google.com/file/d/18GFO6e9vOXunhGgC9tAYQnqIfkH8-Xez/view 
* https://docs.docker.com/compose/django/
* https://www.django-rest-framework.org/#installation
* https://askubuntu.com/questions/477551/how-can-i-use-docker-without-sudo
