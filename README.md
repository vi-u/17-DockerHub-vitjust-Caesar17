# 17-DockerHub-vitjust-Caesar17
>>>> Configure touch-reload to make these changes without needing to restart the Docker container. Commiting to vitjust/caesar17 and push to Docker Hub.

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
Finally you are ready to push your application to Docker Hub using your account.

#First, commit changes of the final version of the project "16-Docker-Flask-Caesar" which is called "docker.test16" to new image "vitjust/caesar17" where "vitjust" is your Docker Hub username

    docker commit -m "added Caesar Flask app" -a "vitjust" docker.test16 vitjust/caesar17

#Second, push it to Docker Hub for other people to be able to use your tool.
To push your image, first log into Docker Hub.

    docker login -u docker-registry-username

#If you did not name commited file with first username/ than you need to do next:

#Note: If your Docker registry username is different from the local username you used to create the image, you will have to tag your image with your registry username. 


    docker tag sammy/caesar17 docker-registry-username/caesar17
    
#To make things easier just use the same name for your local image and your username with DockerHyb.

#Then you may push your own image using:

    docker push docker-registry-username/docker-image-name

#in our case:

    docker push vitjust/caesar17
    
#After pushing an image to a registry, it should be listed on your account’s dashboard.
    
#To try this tool sign in to Docker hub and pull the image:

    docker pull vitjust/caesar17



****
More details about interactions wih Docker Hub are at 
https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-20-04





