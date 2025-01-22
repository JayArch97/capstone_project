CAPSON PROJECT
Julio Acosta
Diego Oliva 


1.5 hour: Docker image is running locally and pushed to Artifact Registry. 

STEPS: 

Gh install and Git installation. 

Firstable, we installed gh using the following command (sudo snap install gh)
And github using the following command sudo apt-get install git.

Docker install 

In order to install Docker, we added the Docker’s official GPG key. 
Sudo apt-get update
Sudo apt-get install ca-certificates curl. 


Dockerfile: 

Docker Image creation command: 
On this step, we created the image in order to run it locally using the command (sudo docker build -t staticwebapp .)


Used the curl command to retrieve the what was in the container that was running locally

sudo docker run -d -p8080:80 staticwebapp

curl http://localhost:8080/


sudo docker build -t us-west2-docker.pkg.dev/acostajulio-dev/capstone-project/test-repo/art-demo:v01 .

 => => naming to us-west2-docker.pkg.dev/acostajulio-dev/capstone-project/test-repo/art-demo:v01        0.0s


We can see the repository named “capstone-project” in the Artifact Registry window in Google cloud. 
In order to create the repository we used the console and type the commands: 

  gcloud artifacts repositories create REPOSITORY \
      --repository-format=docker \
      --location=LOCATION \
      --description="DESCRIPTION" \
      --kms-key=KMS-KEY \
      --immutable-tags \
      --async \
      --disable-vulnerability-scanning



The repository capstone-project was created. 


Then using Cloud Run option, we can select the image to run the project in the cloud using the deploy container/service option:  

The platform processes the image, so we can access the app. 


Once the image is uploaded successfully, it will show the URL, you will be able to visualize the webpage using the URL link. 


This screenshot shows how the port 443(HTTPS) is closed, that’s the reason it’s not working with HTTPS, however, it works with HTTP. 


Then, once the image is uploaded, we make the deployment of the image using the deployment option in the Cloud console, it takes a while to upload the information.

Once the information is submitted we will see the information in workloads, and we can open the name of the deployment to see the details.  				


We can see the resources being used by the deployment. 


Regarding the deployment through App Engine, the information was entered to a yaml file, and it was documented to show html, text, images, javascript and css archives, so the webpage can be presented correctly. 


The SSH does not detect the browser, however, it provides the link, so we can access the website manually.




Resources: 

https://github.com/GNiruthian/Europe-Travel-Website-html-css-js

https://cloud.google.com/artifact-registry/docs/docker/pushing-and-pulling

https://stackoverflow.com/questions/78575606/i-am-unable-to-authenticate-my-account-to-push-images-to-gcp-artifact-registry-d


