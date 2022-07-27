## Host Docker Container with an Api

+ Create the "Container registry"
+ Go to created "Container registry" and to "Access keys"
+ Switch "Admin user" to enabled
+ Remember the passwords and username

+ Create an app and dockerize it -> create an image
+ Use command: "docker login \<azure registry name\>" like: "docker login herbsincontainers.azurecr.io"
+	+ write username and password to login
+ Create a tag for the repository in a certain convention: 
+	+ "docker tag \<imageId or imageName\> \<hostname\>:\<repository-port\>/\<image\>:\<tag\>"
+	+ for instance: "docker tag f80b8386b808 herbsincontainers.azurecr.io/herbs-image:latest"  
		(we can also build with tag [if no docker-compose] "docker build -t herbsincontainers.azurecr.io/herbs-image:latest .")
		+ The best way is to use in docker-compose.yaml file use with tag "image: herbsincontainers.azurecr.io/herbs-image:latest"
+ Push the image to the registry using command: "docker push \<azure registry name\>/\<imagename\>:\<tag\>" 
+	+ like: "docker push herbsincontainers.azurecr.io/herbs-image:latest"
+ Go to "Container registry", to blade "Repositories". Then, select your image

+ Now we create a new resource "Web App for Containers"
+ Remember to select "Azure Container Registry" in docker step. Select registry and image
+ After creating, we have "App Servier" created and we can check if the app is running in container

+ Then we can turn on CD (Continuous Deployment) -> go to "Deployment Center" and select Continuous deployment
	+ The moment we push to the registry a new image, it will be automatically deployed into App Service

To upload a change, just do the change, then build image and then push:
"docker build -t herbsincontainers.azurecr.io/herbs-image:latest ."

## Host Multiple Docker Container with an Api

+ Create an image repository on Azure
+ Create images (with correct tags - ones that include repository name)
+ Push the images to the Azure Repository
+ Create an App Service for Containers
	+ Select in Docker options "Docker Compose"
	+ Select the Azure Container Registry
	+ Upload a configuration file (docker-compose.yaml)
+ Create an resource
+ For Continuous Deployment do the same as for the single container