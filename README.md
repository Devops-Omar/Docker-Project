# Docker-Project

Steps:
1- download / clone from GitHub
2- create Docker-file 
3- create an Image from Docker-file 
3- from image we will run container and expose it using port E.g. 8080
4- access the container from a browser
5- Create new image fom container, which we made plus files we moved in it 
6- Push the image container on Docker Hub


Path for the website: ./Docker-Project/sample-website/sample-website


$ git clone https://github.com/OmarDevopseng/Docker-Prject.git

# after we clone a Docker-Project 

# when we wanna make sure that the file is exist 
$ ls Docker-file/sample-website


# create a file
$vim <name-file>
# after that we write the command into file and then save 
FROM nginx:latest
COPY ./Docker-Project/sample-website  /usr/share/nginx/html/ # copy means we wannn move thw whole folder from host to container we create 
EXPOSE 8080

# Build the image from the Dockerfile and run it publishing port 8080 to be mapped to port 80 on the host

$ docker build -t webseite .
# if we wanna make sure wether the image created or not 
$ Docker images
# now we wanna make a new container from iamge <website> we created
$ docker run -it --rm -d -p 8080:80 --name web website   # about --rm i wanna search about it 

# >> open in browser to test using port 8080 on the local host.

commit the image 



# create an image from our Docker-Project <Container>  
$ docker commit <container_id> [username_account]/[new_image name]:1
# $ docker commit q65ewdhcdc momarmembership/test-docker:v1

$ docker commit q65ewdhcdc<name-container> test-docker<iamge-name> 

# to upload the image to our account to docker registry first log in 
$ docker login

# and then push it to the docker registery >> i will add steps
$ docker push omarmembership/docker-porject

# and then pull it again if you wanna 
docker run -it -rm -d -p 4000:80 --name webseite omarmembership/docker-project
