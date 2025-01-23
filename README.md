CAPSON PROJECT
Julio Acosta
Diego Oliva 


Tutorial Guide on how to deploy a repo on multiple services and then push repo with changes back to Github

STEPS: 

Install Dependencies: 

sudo apt-get install git-all.

# Add Docker's official GPG key:
sudo apt-get update
sudo apt-get install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/debian/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

# Add the repository to Apt sources:
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/debian \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update



sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

	Test:  sudo docker run hello-world // Run this command if you want to verify that it was installed correctly

 
Download the repository: 

git clone https://github.com/GNiruthian/Europe-Travel-Website-html-css-js

Create the dockerfile inside the repo: 

# Use an Nginx base image
FROM nginx:alpine

# Set a working  directory
WORKDIR  /usr/share/nginx/html

#Copy the files
COPY . .

# Expose port 80
EXPOSE 80


CMD ["nginx" , "-g" , "daemon off;"]


Containerize:

docker build . 

Run the image locally:

docker run -d image 

Used the curl command to retrieve the what was in the container that was running locally

curl external ip address

Authenticate:

sudo gcloud auth configure-docker us-west2-docker.pkg.dev

Tag the image:

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

docker tag Image-Id Region-of-Artifact us-west2-docker.pkg.dev (in this case the region is us-west2-docker.pkg.dev)/project-Id/Name-Of-Artifact-repo/Name-you-want-on-docker-file

sudo docker push us-west2-docker.pkg.dev/acostajulio-dev/capstone-project/test-repo/art-demo:v01 .

 => => naming to us-west2-docker.pkg.dev/acostajulio-dev/capstone-project/test-repo/art-demo:v01        0.0s

Then we use the gui to click on the deployment options

Once the image is uploaded successfully, it will show the URL, you will be able to visualize the webpage using the URL link. 

GCE:

This screenshot shows how the port 443(HTTPS) is closed, that’s the reason it’s not working with HTTPS, however, it works with HTTP. 


Then, once the image is uploaded, we make the deployment of the image using the deployment option in the Cloud console, it takes a while to upload the information.

Once the information is submitted we will see the information in workloads, and we can open the name of the deployment to see the details.  				


We can see the resources being used by the deployment. 


Regarding the deployment through App Engine, the information was entered to a yaml file, and it was documented to show html, text, images, javascript and css archives, so the webpage can be presented correctly. 


The cli does not detect the browser, however, it provides the link, so we can access the website manually.




Resources: 

https://github.com/GNiruthian/Europe-Travel-Website-html-css-js

https://cloud.google.com/artifact-registry/docs/docker/pushing-and-pulling

https://stackoverflow.com/questions/78575606/i-am-unable-to-authenticate-my-account-to-push-images-to-gcp-artifact-registry-d


