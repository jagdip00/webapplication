# Steps for Deploying the Entire Flow
I started off by creating a directory for the two files for the static website. The files created were index.html and style.css. I went to ChatGPT and asked it to give me HTML and CSS code for a static website for a company that provides a weather application. I also asked it to give me a company name, include an About Us section, and talk about some of the features of the weather application. I copied the code provided by ChatGPT and added it to the relevant files. 

I then staged the project directory to the Git repository and set the Git global configuration to my GitHub username and email and committed the initial code. I then had to create a repository on GitHub with the name "src" and link my local repository from the environment with my GitHub and push the commit from the local repository to the remote repository on GitHub.

After that, I created a dockerfile outside the 'src' directory, with nginx as the base image, set the nginx working directory, and copied the 'src' folder into the working directory so the web server could access the relevant files and opened it to port 80. I then built the image using the command "docker build -t dockerfile ." and ran the image using the command "docker run -p 8080 80 dockerfile" and opened it to port 8080 and accessed it on localhost to check if everything worked and looks proper and if any changes needed to happen. 

After confirming the website and the dockerfile are configured properly, it's time to push the dockerfile to the docker hub. I used the command "docker tag <your-image-name> <your-dockerhub-username>/<your-repository-name>:<tag>" to tag the image with a name, docker username, repository name and version. Then I used the command "docker login -u <username>" to log into the docker hub and it asked for my password and logged me in. I used the command "docker push <your-dockerhub-username>/<your-repository-name>:<tag>" to push the image to the docker hub and went to the docker hub on my browser to confirm the image was successfully pushed to the docker hub.

Then I had to install the Kind tool that runs kubernetes clusters on the local environment using docker. I then created a cluster using "kind create cluster" and then started creating kuberneted Deployment YAML file which specified the image, which was the one I pushed to the docker hub, I also specified the number of replicas for the deployment. 

# Troubleshooting and Challenges: Solutions and Workarounds

creating the dockerfile outside the src folder
build the image and test the website and make changes - style.css
install kind and learn the basic commands
learn how to port-forward to access the frontend application
