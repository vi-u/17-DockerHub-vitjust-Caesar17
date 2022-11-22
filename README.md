# 17-Updating-Application
>>>> Configure touch-reload to make these changes without needing to restart the Docker container.

    sudo nano uwsgi.ini

#wich contains

    module = main
    callable = app
    master = true
    touch-reload = /app/uwsgi.ini

#make changes to views, Say, change text in home.html a bit.

    @app.route('/')
    def home():
       return "<b>There has been a change</b>"


#Next, if you open your application’s homepage at http://ip-address:56733, you will notice that the changes are not reflected. This is because the condition for reload is a change to the uwsgi.ini file. To reload the application, use touch to activate the condition:

    sudo touch uwsgi.ini

#Now, it will restart with your changes. Tupe in your browser:

    http://localhost:56733
    
******
Finally your are ready to push your application to Docker Hub using your account.

#First, commit changes of the final version of the project "16-Docker-Flask-Caesar" which is called "docker.test16" to new image "vit/caesar16"

    docker commit -m "added Caesar Flask app" -a "vit" docker.test16 vit/caesar16

#Second, push it to Docker Hub for other people to be able to use your tool.

